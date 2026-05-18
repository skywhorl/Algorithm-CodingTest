# [Lv2] JadenCase 문자열 만들기

> **유형:** `#문자열` `#구현`
> **링크:** [12951](https://school.programmers.co.kr/learn/courses/30/lessons/12951)

## 📝 문제 요약
JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다.
문자열 `s`가 주어졌을 때, `s`를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

## 💡 접근/풀이 방식
- 문제 조건에서 `s`는 알파벳과 숫자, 공백문자(" ")로 이루어져 있다. 그렇기에 공백을 기준으로 단어의 시작을 판별할 수 있다.
- 위의 방식을 통해 맨 처음 모든 문자를 소문자로 바꾼 후 공백을 통해 넘어가는 순간만 대문자로 바꿔주면 된다.

## 💻 풀이 코드 (C#)

```C#
using System;

public class Solution {
    public string solution(string s) {
        // 전부 소문자로 변환
        char[] ca = s.ToLower().ToCharArray();
        // 단어의 앞글자 여부
        bool isFirst = true;
        
        for(int i = 0; i < ca.Length; i++)
        {
            // 공백이면 다음이 첫 글자이니 true로 바꾸고 넘기기
            if(ca[i] == ' ')
            {
                isFirst = true;
                continue;
            }
            
            // 대문자로 변경 시 다시 false로
            if(isFirst)
            {
                ca[i] = char.ToUpper(ca[i]);
                isFirst = false;
            }
        }
        
        return new string(ca);
    }
}
```

## ⏱️ 복잡도
- 시간: O(N)
- 공간: O(1) - `ToLower()`, `ToCharArray()`, `new string()`이 각각 입력 길이만큼 메모리 할당 (C# string immutable 특성)