# trocr_small_korean_finetune

이 checkout은 `trocr_small_korean_finetune` 프로젝트 전용 작업 공간이다.

GitHub 저장소를 정본으로 사용하고, 할당받은 서버의 `twentyflags.git` bare repo는 백업 remote로 사용한다.

에이전트는 작업 전에 반드시 `AGENTS.md`를 먼저 읽고, branch, remote, backup ref가 문서와 일치하는지 확인해야 한다.

원격 구성:

```text
origin: https://github.com/atozwizard/trocr_small_korean_finetune.git
backup: ssh://git@210.113.0.140:2345/home/git/projects/twentyflags.git
```

서버 백업 브랜치:

```text
projects/trocr_small_korean_finetune/main
```

작업 전 확인:

```bash
git branch --show-current
git status --short
```

현재 브랜치는 반드시 다음이어야 한다.

```text
main
```

일상 작업은 GitHub로 푸시한다.

```bash
git push
```

서버 백업이 필요할 때만 별도로 푸시한다.

```bash
git push backup HEAD:projects/trocr_small_korean_finetune/main
```
