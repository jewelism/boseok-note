# password

remote의 패스워드를 변경하면 로컬에서 푸시할때 아래와 같은 에러가 난다.

로컬에 저장되어있는 패스워드와 리모트 패스워드가 다르기때문.

```bash
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/jewelism/boseok-note.git/'
```

그냥 아래처럼 초기화해주면 된다.

```bash
git config --unset credential.helper
```

