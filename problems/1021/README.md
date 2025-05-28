# 1021 - 회전하는 큐

## 🔗 문제 링크

[https://www.acmicpc.net/problem/1021](https://www.acmicpc.net/problem/1021)

---

## 📌 문제 설명

지정된 수를 순서대로 뽑기 위해, 원형 큐에서 다음 세 가지 연산을 사용할 수 있습니다:

1. 첫 번째 원소를 제거 (`pop`)
2. 왼쪽으로 한 칸 이동 (`rotate left`)
3. 오른쪽으로 한 칸 이동 (`rotate right`)

큐에서 주어진 순서대로 수를 뽑되, 2번과 3번 연산의 총 횟수를 최소화하는 것이 목표입니다.

---

## 💡 입력 예시

```
10 3
1 2 3
```

## 🎯 출력 예시

```
0
```

---

## ✅ 풀이 요약

- `deque` (양방향 큐)를 사용해 큐의 회전을 효율적으로 구현
- 각 목표 숫자에 대해:
  - 현재 큐에서 해당 숫자의 **인덱스 위치**를 찾고
  - 왼쪽으로 돌리는 게 빠른지, 오른쪽이 빠른지 비교하여 회전
- 연산 횟수 누적하여 출력

---

## 🔍 핵심 로직

```python
from collections import deque

q = deque(range(1, N+1))
count = 0

for num in targets:
    idx = q.index(num)
    if idx <= len(q) // 2:
        q.rotate(-idx)
        count += idx
    else:
        q.rotate(len(q) - idx)
        count += len(q) - idx
    q.popleft()
```

---

## ⏱️ 시간 복잡도

- `deque.index()` 는 O(N)
- 전체 복잡도: **O(N × M)** ≈ 1,000 × 50 = 50,000 → 충분히 통과

---

## 🛠️ 사용 알고리즘/자료구조

- 자료구조: `collections.deque`
- 알고리즘 유형: **시뮬레이션, 큐**

---

## ✍️ 작성자

- [@rladmstj](https://github.com/rladmstj)
