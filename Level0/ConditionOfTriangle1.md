# 삼각형의 완성조건(1)
## [Lv.0 - 120889](https://school.programmers.co.kr/learn/courses/30/lessons/120889?language=csharp)

### 문제 관련
- 가장 큰 변 < 다른 두 변의 합 : 삼각형의 조건
- 가장 큰 수를 찾기, 쉽게 생각하면 세 변을 합하면서 가장 큰 변을 찾은 후 빼기

```c#
using System;

public class Solution {
    public int solution(int[] sides) {
        int answer = 0;
        
        // 세 변의 합
        int sum = 0;
        // 세 변 중 최대 길이
        int max = 0;
        
        // 세 변의 합 구한 후 가장 큰 변 찾기
        foreach(int num in sides)
        {
            sum += num;
            if(num > max)
            {
                max = num;
            }
        }
        
        // [세 변의 합 - 변의 최대 길이], 조건 비교
        answer = (sum - max > max) ? 1 : 2;
        
        return answer;
    }
}
```
