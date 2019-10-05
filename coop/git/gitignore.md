# gitignore

repository에 소스를 올릴때, .gitignore 파일에 특정 디렉토리나 파일 이름을 작성해놓으면,

그 디렉토리나 파일은 제외된다.

.gitignore 예시

```text
/node_modules
.DS_STORE
.idea

.env
```

## 이미 커밋된 파일을 git ignore 하는 방법

gitignore파일을 수정하고 다음명령어를 실행한다.

```bash
git rm --cached /path/to/file
```

