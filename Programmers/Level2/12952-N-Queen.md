# [Lv2] N-Queen

> **유형:** `#구현` `#DFS`
> **링크:** [12952](https://school.programmers.co.kr/learn/courses/30/lessons/12952)

## 📝 문제 요약
체스판의 가로 세로의 길이 `n`이 매개변수로 주어질 때, `n`개의 퀸이 조건에 만족 하도록 배치할 수 있는 방법의 수를 return하는 solution함수를 완성해주세요.

## 💡 접근/풀이 방식
- 2차원 배열(O(N²) 공간) 대신 1차원 배열(O(N) 공간)로 표현했다.
- 여왕의 배치 횟수와 배치 가능 점검 횟수는 `n`에 따라 바뀌므로 배치와 점검을 재귀함수(DFS) 형태로 구현했다.
- 안전성 검사 (`IsSafe`):
  - **같은 열**: `col[i] == col[row]`
  - **같은 대각선**: `|i - row| == |col[i] - col[row]|` — 대각선은 기울기 ±1이므로 행 차이와 열 차이의 절댓값이 같다.

## 💻 풀이 코드 (C#)

```C#
using System;

public class Solution {
        // 각 열에 배치된 여왕들의 위치
        int[] col;
        // 보드 범위용 변수
        int end;
        // 배치 가능 케이스
        int answer = 0;

    public int solution(int n) {

        // 전역 변수 값 할당
        col = new int[n];
        end = n;
        
        // 0번째부터 n-1번째 행까지 여왕 배치
        SetQueen(0);

        return answer;
    }
    
    /// 여왕 배치
    private void SetQueen(int row) {
        // 다 배치 했으면 배치 조건을 모두 충족한 것이므로 정답 추가 및 종료
        if(row == end)
        {
            answer++;
            return;
        }
        
        for(int i = 0; i < end; i++)
        {
            // 해당 행(row)에서 i번째에 여왕 배치
            col[row] = i;
            
            // 해당 열에 배치한 여왕이 안전하면 다음으로 넘기기
            if(IsSafe(row)) SetQueen(row+1);
        }
    }
    
    /// 이전에 배치한 여왕들의 위치 비교를 통해 현재 배치한 위치가 안전한지 확인
    private bool IsSafe(int row) {
        // 처음에 배치한 행부터 지금 전까지의 행까지 배치한 여왕과의 위치 비교
        for(int i = 0; i < row; i++)
        {
            // 같은 열 || 대각선에 존재 시 안전하지 않음
            if(col[i] == col[row] || Math.Abs(i - row) == Math.Abs(col[i] - col[row]))
                return false;
        }
        // 위의 반복분을 통과 했다는 건 안전하다는 의미
        return true;
    }
}
```

## ⏱️ 복잡도
- 시간: O(N!) - 각 행마다 N개 위치 시도, 백트래킹 가지치기로 실제로는 훨씬 작음
- 공간: O(N) -  `col` 배열 + 재귀 호출 스택 깊이 N