# [Lv2] H-Index

> **유형:** `#정렬` `#구현`
> **링크:** [42747](https://school.programmers.co.kr/learn/courses/30/lessons/42747)

## 📝 문제 요약
어떤 과학자가 발표한 논문 n편 중, `h`번 이상 인용된 논문이 h편 이상이고 나머지 논문이 `h`번 이하 인용되었다면 `h`의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 `citations`가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

## 💡 접근/풀이 방식
- 인용된 논문을 어떠한 경우에서든 최대한 빨리 찾기 위해서 배열을 오름차순으로 정리했다.

## 💻 풀이 코드 (C#)

```C#
using System;

public class Solution {
    public int solution(int[] citations) {
        // 오름차순으로 인용 횟수를 비교
        Array.Sort(citations);
        int n = citations.Length;
        
        for(int i = 0; i < n; i++)
        {
            // 인용된 논문(뒤에서부터)
            int h = n-i;
            
            // h번 이상 인용된 논문이 h편 이상인 경우
            if(citations[i] >= h)
                return h;
        }
        // 모든 논문 인용 횟수가 0일 때
        return 0;
    }
}
```

## ⏱️ 복잡도
- 시간: O(N log N) - `Array.Sort()`가 지배항
- 공간: O(log N) - 정렬 내부 재귀 스택