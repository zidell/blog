---
layout: post
title: "파이썬으로 시작하는 데이터 분석: pandas 기초부터 실전까지"
date: 2024-12-05 14:20:00 +0900
categories: [프로그래밍, 데이터분석]
tags: [python, pandas, 데이터분석, numpy]
---

데이터 분석은 현대 비즈니스의 핵심 역량이 되었습니다. 오늘은 파이썬의 강력한 데이터 분석 라이브러리인 pandas의 기본 사용법을 알아보겠습니다.

## pandas 시작하기

```python
import pandas as pd
import numpy as np

# 데이터프레임 생성
df = pd.DataFrame({
    '이름': ['김철수', '이영희', '박지민'],
    '나이': [25, 28, 22],
    '직업': ['개발자', '디자이너', '학생']
})
```

## 기본 데이터 조작

### 데이터 필터링
```python
# 나이가 25살 이상인 사람 찾기
filtered_df = df[df['나이'] >= 25]
```

### 데이터 정렬
```python
# 나이순으로 정렬
sorted_df = df.sort_values('나이', ascending=False)
```

## 데이터 분석 실전 예제

실제 데이터를 활용한 간단한 분석을 해보겠습니다.

### 기술 통계량 계산
```python
# 나이의 평균, 중앙값 등 계산
age_stats = df['나이'].describe()
```

### 그룹별 분석
```python
# 직업별 평균 나이 계산
job_age_mean = df.groupby('직업')['나이'].mean()
```

## 시각화하기

matplotlib과 함께 사용하면 데이터를 시각적으로 표현할 수 있습니다.

```python
import matplotlib.pyplot as plt

# 직업별 나이 분포 시각화
df.boxplot(column='나이', by='직업')
plt.show()
```

## 실무에서 자주 사용하는 팁

1. 결측치 처리하기
2. 데이터 전처리 방법
3. 효율적인 데이터 병합
4. 성능 최적화 방법

pandas를 활용하면 복잡한 데이터도 쉽게 다룰 수 있습니다. 계속해서 실습하고 경험을 쌓아보세요!
