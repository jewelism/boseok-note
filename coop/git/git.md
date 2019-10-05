# git

git이 설치되어있지않다면, mac 환경이라면 우선 homebrew를 이용하여 git을 설치하자.

```bash
brew install git
```

git flow를 사용한다면

```bash
brew install git-flow
```

```bash
git config --global user.name "jewelism"
git config --global user.email "boseokjung@gmail.com"
```

## pr을 통해 코드 리뷰하는 절차

1. 원본의 remote repository를 자신의 repository로 fork
2. 자신의 git repository clone
3. git remote add upstream 원본 원격 저장소의 주소
4. 소스수정..
5. git add 수정한파일 \(git add . 은 모두\)
6. git commit -m "커밋메시지"
7. git pull upstream 브랜치이름\(3번에서 추가한 upstream이라는 이름과 일치해야함\)
8. git push origin 브랜치이름
9. 원격저장소 웹에서 pull request 작성

