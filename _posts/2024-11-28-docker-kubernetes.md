---
layout: post
title: "Docker와 Kubernetes로 시작하는 컨테이너 오케스트레이션"
date: 2024-11-28 14:30:00 +0900
categories: [개발, 인프라]
tags: [docker, kubernetes, devops, 컨테이너]
---

현대 클라우드 네이티브 환경에서 필수가 된 Docker와 Kubernetes의 기본 개념과 활용법을 알아봅니다.

## Docker 기초

### 기본 명령어
```bash
# 이미지 빌드
docker build -t myapp:1.0 .

# 컨테이너 실행
docker run -d -p 8080:80 myapp:1.0

# 컨테이너 목록 확인
docker ps
```

### Dockerfile 작성
```dockerfile
FROM node:16-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

## Kubernetes 구성요소

### 핵심 개념
1. Pod
2. Service
3. Deployment
4. ConfigMap
5. Secret

### 기본 매니페스트 파일
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: myapp:1.0
        ports:
        - containerPort: 80
```

## 실전 활용

### 스케일링
```bash
# 수평적 스케일링
kubectl scale deployment myapp --replicas=5

# 자동 스케일링 설정
kubectl autoscale deployment myapp --min=2 --max=10 --cpu-percent=80
```

### 롤링 업데이트
```bash
# 새 버전 배포
kubectl set image deployment/myapp myapp=myapp:2.0

# 롤백
kubectl rollout undo deployment/myapp
```

## 모니터링과 로깅

### 프로메테우스 설정
```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: myapp-monitor
spec:
  selector:
    matchLabels:
      app: myapp
  endpoints:
  - port: metrics
```

### 로그 수집
- EFK 스택 구성
- Loki 활용
- CloudWatch 연동

## 보안 설정

### 네트워크 정책
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: myapp-policy
spec:
  podSelector:
    matchLabels:
      app: myapp
  policyTypes:
  - Ingress
  - Egress
```

### 시크릿 관리
1. 암호화된 시크릿 사용
2. 외부 시크릿 관리자 연동
3. RBAC 설정

## 운영 팁

### 리소스 관리
- 리소스 쿼터 설정
- 리밋 레인지 활용
- HPA 구성

### 트러블슈팅
1. 로그 분석
2. 이벤트 확인
3. 디버그 컨테이너 활용

컨테이너 오케스트레이션은 현대 애플리케이션 운영의 핵심입니다. 계속해서 학습하고 발전시켜 나가세요.
