## revert
- git revert 명령어를 사용해 이미 작성한 커밋을 지울 수 있다.
- rebase -i 명령어나 reset 명령어로 커밋을 삭제할 수도 있지만, 커밋이 이미 공개된 상태라면 이러한 삭제 작업을 함부로 하기 어렵다.  
이러한 경우 revert 명령어로 특정 커밋(B)의 내용을 지우는 새로운 커밋(B')을 만들어 보다 안전하게 처리할 수 있다.

![image](https://user-images.githubusercontent.com/57171304/185043193-e1693381-f4cc-44b3-84b0-242b6646e32b.png)
<br>

## 사용할 수 있는 상황
- 이전에 작성한 커밋을 안전하게 지우고 싶을 때
<br>

## 예시
![image](https://user-images.githubusercontent.com/57171304/185045249-d55763a3-6116-4547-b233-9ee30ff39b3d.png)
<br>

> ### 기존 git log
<img width="533" alt="image" src="https://user-images.githubusercontent.com/57171304/185045933-396531d6-0297-4c10-a26a-a33effdd3220.png">
<br>

> ### 기존 파일 내용
<img width="366" alt="image" src="https://user-images.githubusercontent.com/57171304/185046223-5d807ae1-1838-405d-9ff9-cfc3ab790d7b.png">
<br>

> ### git revert 실행
```
$ git revert HEAD  <- 가장 최근 커밋 내용을 지우는 커밋 추가
```
<br>

> ### revert 적용 후 git log
<img width="552" alt="image" src="https://user-images.githubusercontent.com/57171304/185055465-c206e557-818d-41f1-bf2f-ca032b447992.png">
<br>

![image](https://user-images.githubusercontent.com/57171304/185055595-65c0fc14-ce17-4432-b93e-a9de01afb8e0.png)

<br>

[출처] https://backlog.com/git-tutorial/kr/
