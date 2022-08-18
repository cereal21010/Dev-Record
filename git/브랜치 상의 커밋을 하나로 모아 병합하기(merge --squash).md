## marge --squash
- squash 옵션으로 병합하면 해당 브랜치의 커밋 전체를 통합한 커밋이 추가 됩니다.
![image](https://user-images.githubusercontent.com/57171304/185295893-1271498b-d831-478f-baf8-af9a641b0917.png)
<br>

## 사용할 수 있는 상황
- 토픽 브랜치 안의 커밋을 한꺼번에 모아서 통합 브랜치에 병합하고자 할 때
<br>

## 예시
![image](https://user-images.githubusercontent.com/57171304/185295966-f8d6f227-bb66-4cc1-b77e-85cc01f18a7e.png)
<br>

>### merge --squash 실행
```
$ git checkout master
$ git merge --squash issue1
```
###### *병합하려는 브랜치로 이동 후 merge --squash 명령어 실행
<br>

- 충돌이 발생했다면 충돌난 파일을 수정 후 커밋한다.
```
$ git add sample.txt
$ git commit
```


[출처] https://backlog.com/git-tutorial/kr
