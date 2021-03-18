# 이미-push한-파일에-gitignore-적용하기.md

작업을 하다보면 git repo에 올리고 싶지않은 파일이 생기곤 한다.
하지만 매번 .gitignore에 미리 작성하기는 쉽지 않다. 이미 push한 파일 때문에
곤란을 겪은 기억이 여러번 있다.

결론(해결책)은 아래와 같다.

```
git rm -r --cached <fileName>
git add <fileName>
git commit -m 'Update .gitignore'
```

git rm의 `--cached` 옵션을 사용하면 로컬을 제외한 원격 저장소의 파일만 삭제된다.
