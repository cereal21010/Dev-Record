## cherry-pick
- cherry-pick을 이용하면 다른 브랜치에서 지정한 커밋을 복사하여 현재 브랜치로 가져올 수 있다
![image](https://user-images.githubusercontent.com/57171304/185094980-43d222d7-9df7-40cd-8d53-fd0720338e84.png)
<br>

## 사용할 수 있는 상황
- 특정 브랜치에 잘못 추가한 커밋을 올바른 브랜치로 옮기려고 할 때
- 다른 브랜치의 커밋을 현재 브랜치에도 추가하고 싶을 때
<br>

## 예시
![image](https://user-images.githubusercontent.com/57171304/185097410-0cb7ecc5-b467-4489-8897-a8a477ccee3e.png)
###### *예제에서는 master 와 issue1 브랜치가 존재한다
<br>

>### cherry-pick 실행
- master 브랜치로 이동 (복사된 커밋을 적용하려는 브랜치로 이동) 후 cherry-pick 명령어 실행
```
$ git checkout master  <- 복사된 커밋을 적용하려는 브랜치로 
$ git cherry-pick 99daed2  <- 커밋id 값, git log 명령어로 확인 가능
```

- 커밋 내용에 따라 충돌이 발생할 수 있다. 충돌이 생길 경우 충돌 부분을 수정한 후 커밋을 진행하면 된다.
```
$ git add sample.txt
$ git commit <- 기본적으로 복사한 커밋의 메세지 입력되 있고 명령어 입력 후 수정할 수 있다
```
