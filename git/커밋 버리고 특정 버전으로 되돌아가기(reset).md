## reset
- reset 명령어를 사용해 필요 없어진 커밋들을 버릴 수 있다. 옵션으로 실행 모드를 지정하여 'HEAD', 인덱스, 작업트리(local) 내용을 함께 되돌릴지 여부를 선택할 수 있다.  
![image](https://user-images.githubusercontent.com/57171304/185082487-e85046a0-61ca-4fae-bc06-3fc3e8e9b2e9.png)

- 모드는 기본적으로 'mixed'가 지정된다.  
![image](https://user-images.githubusercontent.com/57171304/185082633-ba97f13f-834c-4e32-b9ca-7a665eb61700.png)

<br>

## 사용할 수 있는 상황
- 커밋만 되돌리고 싶을 때(soft)
- 변경한 인덱스의 상태를 원래대로 되돌리고 싶을 때(mixed)
- 최근 커밋을 완전히 버리고 이전 상태로 되돌리고 싶을 때(hard)

<br>

## 예시
![image](https://user-images.githubusercontent.com/57171304/185087382-50129268-dc93-4d13-b649-51595e621b7f.png)

>### 기존 git log
<img width="527" alt="image" src="https://user-images.githubusercontent.com/57171304/185087484-352a0b29-ffa3-4646-8111-98bdb29233fa.png">
<br>

>### 기존 파일 내용
<img width="366" alt="image" src="https://user-images.githubusercontent.com/57171304/185087747-33ce547b-421b-4a88-852b-43f5b5a152c2.png">
<br>

>### git reset 실행
```
$ git reset --hard HEAD~~  <- HEAD기준 2개 이전 커밋들을 hard 옵션으로 삭제
``` 
<br>

>### reset 실행 후 git log
<img width="522" alt="image" src="https://user-images.githubusercontent.com/57171304/185089728-7df9e5ec-cad1-44c3-a48b-6c642e4d1bbb.png">
<br>

>### reset 실행 후 파일 내용
<img width="365" alt="image" src="https://user-images.githubusercontent.com/57171304/185090303-74fbe950-eb52-432d-955e-93fb6c14ffd8.png">
<br>

## reset 실행 전 상태로 되돌리기
- reset 전의 커밋은 'ORIG_HEAD' 라는 이름으로 참조할 수 있습니다.
```
$ git reset --hard ORIG_HEAD  <- reset 전의 커밋으로 돌아간다
```



