# @ModelAttribute 어노테이션의 기능과 커맨드 객체

### 커맨드 객체
- 커맨드 객체란 HttpServletRequest를 통해 들어온 요청 파라미터들을 setter 메서드를 이용해
  객체에 정의되어있는 속성에 바인딩 되는 객체를 의미한다.
  
- 커맨드 객체는 보통 DTO(VO)를 의미하며, HttpServletRequest로 받아오는 요청 파라미터의 key 값과
  동일한 이름의 속성과 setter 메서드를 가지고 있으면 스프링이 내부적으로 알아서 바인딩을 시켜준다. 

- 장점
	- 코드 양과 가독성 측면에서 HttpServletRequest 나 @RequestParam 을 사용하는 것보다 좋다. 
	
---	
	
### @ModelAttribute
- @ModelAttribute는 커맨드 객체와 같이 요청 파라미터들을 객체 프로퍼티에 바인디 시켜준다.
  하지만 생략하여도 커맨드 객체를 이용해 바인딩이 된다.(@RequestParam 도 생략해도 사실상 바인딩이 가능하다.)
	- 스프링이 내부적으로 String이나 int등은 @RequestParam, 복잡한 객체들은 @ModelAttribute 가 생략했다고 간주하기 때문이다.
	- 스프링이 간당한 숫자나 문자로 전달된 요청 파라미터를 복잡한 객체로 변환할 수도 있기 때문에 무조건 생략하는 것은 위험하다.

1. 파라미터 객체 옆에 @ModelAttribute 사용하는 경우
```
@PostMapping("/ins")
public String ins(@ModelAttribute User user, Model model) {
  String name = user.getUserName();
  String phone = user.getPhone();
  int age = user.getAge();
  
  // user 객체를 모델에 담는 코드를 작성하지 않아도, 담겨져 있다.
  // 내부적으로 model.addAttribute("user", user); 로 담는다.
  // 만약 객체명과 변수명이 @ModelAttribute UserVo user 로 되어있는 경우에는 어떻게 담길까?
  // 클래스명을 기준으로 카멜케이스를 적용하여 model.addAttribute("userVo", user); 로 담는다.
  
  return REDIRECT_LIST;
}
```
- model에 객체를 담아준다.

- @ModelAttribute 가 붙은 파라미터를 처리할 때 @RequestParam 과 달리 검증(Validation) 작업을 내부적으로 진행 한다.
	- @RequestParam 의 경우 파라미터의 타입 변환이 실패하면 Http 400 Bad Request 응답이 클라이언트로 가게된다.
	  (org.springframework.beans.TypeMismatchException 예외를 처리하는 예외 리졸버를 추가해 메시지로 보여줄 수 있다.)
	- @ModelAttribute 는 타입 변환에 실패해도 작업은 계속되며 BindingException 타입의 객체에 담겨서 컨트롤러로 전달된다.
	- 따라서 @ModelAttribute 를 통해서 폼의 정보를 전달 받은 경우 Errors객체나 BingingResult 객체를 @ModelAttribute 가
	  붙은 파라미터 바로 뒤에 선언해서 검증 처리를 실시한다.
	- <U>Errors 나 BindingResult 는 자신의 바로 앞에 있는 파라미터 검증에서 발생한 오류들만 전달해주기 때문에 @Valid 나 @Validated, @ModelAttribute 가 붙은 파라미터 바로 뒤에 선언되어야 합니다.</U>
	
	
2. 메서드 위에 @ModelAttribute 가 사용되는 경우에는
- 컨트롤러에서 메서드 위에 @ModelAttribute 가 사용되는 경우는, 해당 컨트롤러 내의 어떠한 핸들러 메서드들보다 먼저 동작하게 된다.
```
/**
 * @ModelAttribute 메서드가 먼저 동작하기 때문에,
 * 다른 핸들러 메서드에서 model 에 담겨져있는 user 키값을 이용하여 user 객체를 꺼내서 쓸 수 있다.
 */
@ModelAttribute("user")
public String initUser() {
  // 내부적으로 model.addAttribute("user", userService.findUser(FIRST_USER_SEQ)); 형태로 담는다.
  return userService.findUser(FIRST_USER_SEQ); 
}
```
- 따라서 여러 핸들러 메서드에서 공통으로 쓰이며, View 단에서도 꺼내 쓸일이 있는 것들을 처리하기 위해 사용한다.










