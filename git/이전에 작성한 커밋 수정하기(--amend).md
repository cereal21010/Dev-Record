## commit --amend
- --amend 옵션을 추가해 커밋을 실행하면, 현재 사용중인 브랜치의 이전 커밋 내용에 새로운 내용을 추하거나 설명을 추가할 수 있다.
<br/>    

## 사용할 수 있는 상항
- 누락된 파일을 새로 추가하거나 기존의 파일을 업데이트 해야할 때
- 이전 커밋의 설명을 변경하고 싶을 때
<br/>

## 예시
![image](https://user-images.githubusercontent.com/57171304/185010079-2dd9c70b-e18a-4368-9bf8-a96682eedff7.png)
###### **아래의 콘솔 이미지의 커밋 고유번호가 위의 이미지와 다른건 무시*  
  
  
#### 기존 git log
<img width="523" alt="image" src="https://user-images.githubusercontent.com/57171304/185010758-988ee7ef-3da8-4bbd-b4e7-c04718ad5082.png">
  
  
#### 파일 수정
<img width="368" alt="image" src="https://user-images.githubusercontent.com/57171304/185013520-a2aaeeb5-47c8-4c66-928e-dc23fb4a61fa.png">
  
  
#### commit --amend 실행
<img width="621" alt="image" src="https://user-images.githubusercontent.com/57171304/185013627-3365d00b-d67d-4845-b1b9-bb21e737cebc.png">
  
  
#### commit --amend를 적용 후 git log
<img width="515" alt="image" src="https://user-images.githubusercontent.com/57171304/185013745-d0c05cab-c440-40d0-9cb7-8ae4cb60d336.png">

###### **커밋 메세지가 바뀌고 커밋에 포함된 파일 내용도 바뀌었다*

![image](https://user-images.githubusercontent.com/57171304/185013880-81d2e693-9d6e-4ec7-af9b-acd1702ccec6.png)

