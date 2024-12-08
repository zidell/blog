---
layout: post
title: "Next.js와 TypeScript로 만드는 현대적인 웹 애플리케이션"
date: 2024-12-01 10:30:00 +0900
categories: [개발, 웹개발]
tags: [nextjs, typescript, react, frontend]
---

Next.js와 TypeScript의 조합으로 안정적이고 확장 가능한 웹 애플리케이션을 구축하는 방법을 알아보겠습니다.

## 프로젝트 설정

```bash
npx create-next-app@latest my-app --typescript
cd my-app
npm run dev
```

## 기본 구조 설정

```typescript
// pages/index.tsx
import type { NextPage } from 'next'

interface Post {
  id: number;
  title: string;
  content: string;
}

const Home: NextPage = () => {
  const posts: Post[] = [
    { id: 1, title: '첫 번째 글', content: '내용입니다.' }
  ];

  return (
    <div>
      {posts.map(post => (
        <article key={post.id}>
          <h2>{post.title}</h2>
          <p>{post.content}</p>
        </article>
      ))}
    </div>
  );
}

export default Home;
```

## API 라우트 구현

```typescript
// pages/api/posts.ts
import type { NextApiRequest, NextApiResponse } from 'next'

export default async function handler(
  req: NextApiRequest,
  res: NextApiResponse
) {
  if (req.method === 'GET') {
    // DB 조회 로직
    res.status(200).json({ posts: [] })
  }
}
```

## 타입 안전성 확보

### 커스텀 타입 정의
```typescript
// types/index.ts
export interface User {
  id: string;
  name: string;
  email: string;
}

export interface Comment {
  id: string;
  userId: string;
  content: string;
}
```

## 서버사이드 렌더링 활용

```typescript
export const getServerSideProps: GetServerSideProps = async (context) => {
  const res = await fetch('https://api.example.com/data')
  const data = await res.json()

  return {
    props: {
      data,
    },
  }
}
```

## 성능 최적화

### 이미지 최적화
```typescript
import Image from 'next/image'

export default function Profile() {
  return (
    <Image
      src="/profile.jpg"
      alt="Profile"
      width={500}
      height={300}
      priority
    />
  )
}
```

## 배포 고려사항

1. 환경변수 설정
2. 빌드 최적화
3. CI/CD 파이프라인

## 실전 팁

- 강력한 타입 체크 활용하기
- 컴포넌트 재사용성 높이기
- 성능 모니터링하기

Next.js와 TypeScript의 조합은 현대 웹 개발의 강력한 도구입니다.
