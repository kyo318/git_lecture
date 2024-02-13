#git #github

git push 할 때 password 인증방식이 personal access token 방식으로 바뀜

1. github -> settings 클릭

![[Pasted image 20231015235812.png]]

2. Developer settings 클릭 
3. Personal access tokens 클릭
4. Generate new token 클릭
5. Token 설정
     repo나 user 관련 내용은 전부 체크
6. Generate Token 클릭
    **창을 나가지 말고 토큰을 꼭 복사한다!**
7. Mac KeyChain 삭제
    command + space 누르고 keychain 검색
    여기서 github 검색하고 만약 있다면 삭제 
8. 터미널에서 user정보 입력
    git config --global user.name kyo318
    git config --global user.email "choiykyo@gmail.com"
9. git commit 후 git push 하면
    $ Username for https://github.com: 
    $ Password for https://github.com/kyo318: 
    Username에는 아이디를 적고
    **Password 부분에는 복사했던 Personal access token을 입력한다**
10. git push 정상 작동 확인!