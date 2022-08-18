## rebase -i
- rebase 명령어에 i 옵션을 지정해 커밋을 다시 쓰거나 다른 커밋과 바꿔 넣을 수 있다. 또 특정 위치의 커밋을 삭제하거나 여러 커밋을 하나로 통합할 수도 있다.
![image](https://user-images.githubusercontent.com/57171304/185101377-97a049ab-13cc-4946-8231-3ad610a36a7b.png)
<br>

## 사용할 수 있는 상황
- push 하기 전에 이전의 커밋 내용을 정리하고자 할 때
- 그룹으로 묶을 수 있는 커밋들을 알기 쉽게 하나로 통합하려고 할 때
- 이전 커밋에 누락된 파일들을 나중에 추가하고자 할 때
<br>


## 예시
![image](https://user-images.githubusercontent.com/57171304/185102070-91be507b-cb01-4e3b-b72e-4635f497a0a9.png)
<br>


### 1.커밋 통합하기  
<br>

>### rebase -i 실행
```
$ git rebase -i HEAD~~
```
- 명령어를 실행하면 텍스트 에디터가 열리고 HEAD에서 'HEAD~~'까지의 커밋이 아래 이미지와 같이 표시된다.
<img width="420" alt="image" src="https://user-images.githubusercontent.com/57171304/185270665-c5dff1d2-a0fc-4ef2-b99b-ce0883d33ffb.png">

- 두 번째 줄의 'pick'문자를 **squash**로 변경하고 저장/종료합니다.
<br>

>### rebase -i 적용 후 git log
<img width="522" alt="image" src="https://user-images.githubusercontent.com/57171304/185271077-556195ca-8863-4312-a064-430b02167ac3.png">

###### *마지막 두개의 커밋이 하나로 통합된걸 확인할 수 있다.

### 2.커밋 수정하기

>### rebase -i 실행
```
$ git rebase -i HEAD~~
```
- 명령어를 실행하면 텍스트 에디터가 열리고 HEAD에서 'HEAD~~'까지의 커밋이 아래 이미지와 같이 표시된다.
<img width="420" alt="image" src="https://user-images.githubusercontent.com/57171304/185270665-c5dff1d2-a0fc-4ef2-b99b-ce0883d33ffb.png">

- 첫 번째 줄의 'pick'문자를 '**edit**'로 변경하고 저장/종료합니다. 그러면 아래와 같은 내용이 출력되고 수정할 커밋이 체크아웃된 상태가 된다.
<img width="371" alt="image" src="https://user-images.githubusercontent.com/57171304/185278589-e30258dd-5a79-453d-b6ab-0da488ffa57c.png">
<br>

- 수정할 커밋(commit 설명 추가)의 내용(파일)을 수정하고 아래 명령어로 변경한 내용을 저장한다.
```
$ git add sample.txt
$ git commit --amend
```
- 변경한 내용을 저장 후 커밋 작업이 종료됐다고 알려줘야한다. --continue 옵션을 지정하여 rebase 를 실행한다.
```
$ git rebase --continue
```
###### *이 때, 커밋에서 충돌이 발생할 수 있다. 그럴 때는 충돌 부분을 수정 후 add와 rebase --continue를 실행하면 된다. 커밋은 필요 없으므로 실행하지 않는다.<br>만약 도중에 rebase 작업을 중지하려면 rebase --abort 옵션을 지정해 실행한다.

<br>


<br>

[출처] https://backlog.com/git-tutorial/kr/
