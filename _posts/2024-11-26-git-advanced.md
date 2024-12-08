---
layout: post
title: "Git 고급 기능 활용하기: 리베이스부터 서브모듈까지"
date: 2024-11-26 11:10:00 +0900
categories: [개발, 버전관리]
tags: [git, github, 개발도구, 협업]
---

Git의 고급 기능들을 활용하여 더 효율적인 버전 관리와 협업을 할 수 있습니다.

## Interactive Rebase

### 기본 사용법
```bash
# 최근 3개의 커밋 수정
git rebase -i HEAD~3

# 특정 커밋부터 수정
git rebase -i <commit-hash>
```

### 주요 명령어
- pick: 커밋 유지
- reword: 커밋 메시지 수정
- edit: 커밋 내용 수정
- squash: 이전 커밋과 합치기
- drop: 커밋 삭제

## Git Submodules

### 서브모듈 추가
```bash
git submodule add <repository-url> <path>
git submodule init
git submodule update
```

### 서브모듈 업데이트
```bash
# 모든 서브모듈 업데이트
git submodule update --remote

# 특정 서브모듈 업데이트
git submodule update --remote <submodule-name>
```

## Git Hooks

### 로컬 훅 설정
```bash
#!/bin/sh
# .git/hooks/pre-commit

# 코드 스타일 검사
npm run lint

# 테스트 실행
npm test
```

### 주요 훅 종류
1. pre-commit
2. post-commit
3. pre-push
4. post-merge

## Git Worktree

### 여러 브랜치 동시 작업
```bash
# 새 작업 트리 생성
git worktree add ../path-to-new-tree branch-name

# 작업 트리 목록 확인
git worktree list

# 작업 트리 제거
git worktree remove path-to-tree
```

## Git Bisect

### 버그 찾기
```bash
# 이진 탐색 시작
git bisect start

# 현재 상태가 나쁨을 표시
git bisect bad

# 정상 작동하는 커밋 지정
git bisect good <commit-hash>
```

## Git Cherry-pick

### 특정 커밋만 가져오기
```bash
# 단일 커밋 가져오기
git cherry-pick <commit-hash>

# 여러 커밋 가져오기
git cherry-pick <commit-hash-1> <commit-hash-2>
```

## Git Reflog

### 작업 기록 복구
```bash
# reflog 확인
git reflog

# 특정 시점으로 복구
git reset --hard HEAD@{2}
```

## 고급 설정

### Git Attributes
```gitattributes
# .gitattributes
*.txt diff=text
*.jpg diff=exif
```

### Git Config
```bash
# 별칭 설정
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```

## 성능 최적화

### 대용량 저장소 관리
1. Git LFS 사용
2. Shallow Clone 활용
3. Sparse Checkout 설정

### 캐시 관리
```bash
# 캐시 정리
git gc

# 캐시 최적화
git prune
```

이러한 고급 기능들을 잘 활용하면 더욱 효율적인 개발 워크플로우를 구축할 수 있습니다.
