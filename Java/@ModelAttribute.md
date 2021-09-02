# @ModelAttribute 어노테이션의 기능과 커맨드 객체

### 커맨드 객체
+ 커맨드 객체란 HttpServletRequest를 통해 들어온 요청 파라미터들을 setter 메서드를 이용해
  객체에 정의되어있는 속성에 바인딩 되는 객체를 의미한다.
  
+ 커맨드 객체는 보통 DTO(VO)를 의미하며, HttpServletRequest로 받아오는 요청 파라미터의 key 값과
  동일한 이름의 속성과 setter 메서드를 가지고 있으면 스프링이 내부적으로 알아서 바인딩을 시켜준다. 

+ 장점
	+ 코드 양과 가독성 측면에서 HttpServletRequest 나 @RequestParam 을 사용하는 것보다 좋다. 
	
	
	
### @ModelAttribute
+ @ModelAttribute는 커맨드 객체와 같이 요청 파라미터들을 객체 프로퍼티에 바인디 시켜준다.
  하지만 생략하여도 커맨드 객체를 이용해 바인딩이 된다.(@RequestParam 도 생략해도 사실상 바인딩이 가능하다.)
	+ 스프링이 내부적으로 String이나 int등은 @RequestParam, 복잡한 객체들은 @ModelAttribute 가 생략했다고 간주하기 때문이다.
	+ 스프링이 간당한 숫자나 문자로 전달된 요청 파라미터를 복잡한 객체로 변환할 수도 있기 때문에 무조건 생략하는 것은 위험하다.

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

	
	
	
