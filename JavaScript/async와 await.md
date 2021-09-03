# async와 await

### async & await 란
- 기존 비동기 처리 방식인 콜백 함수와 프로미스의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성할 수 있게 해주는 자바스크립트의 비동기 처리 패턴

### async & await 와 콜백 함수의 차이
-콜백 함수
```
function logName() {
  var user = fetchUser('domain.com/users/1', function(user) {
    if (user.id === 1) {
      console.log(user.name);
    }
  });
}
```
- async & await
```
async function logName() {
  var user = await fetchUser('domain.com/users/1');
  if (user.id === 1) {
    console.log(user.name);
  }
}
```

### async & await 기본 문법
```
async function 함수명() {
  await 비동기_처리_메서드_명();
}
```
- 함수 앞에 async 라는 예약어를 붙인 후, 내부 로직 중 Http 통신을 하는 비동기처리 코드 앞에 await 를 붙인다.
- await 가 붙은 비동기처리 메서드는 꼭 프로미스 객체를 반환해야 동작한다.
  (axios 등 프로미스를 반환하는 api 호출 함수에 주로 사용)

### async & await 예외처리
```
async function logTodoTitle() {
  try {
    var user = await fetchUser();
  } catch (error) {
    console.log(error);
  }
}
```
- async & await 는 try catch로 예외처리가 가능합니다.
- 네트워크 통신 오류, 타입 오류 등 전반적인 오류들을 잡아낼 수 있고, error 객체에 담아 처리 할 수 있습니다.  
