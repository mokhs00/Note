# **[프로그래머스 | 해시 Lv.1] 완주하지 못한 선수 (Java)**

# 📖문제설명

**자세한 문제 설명은 아래 링크를 참고해주세요.**

**[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42576)**

[문제 설명 이미지]

# 🤔문제 풀이 방식
``` js
단 한 명의 완주하지 못 한 선수를 찾아라
*동명이인이 있을 수 있을 수 있으니 주의하자.
        
`HashMap`을 이용한다.
`key`는 `이름`, `value`는 `count`로 두고 
`participant` 배열을 돌면서 `count`를 기록
        
`completion`를 돌면서 'HashMap'의 'key'와 매칭되는 사람의 'count'를 줄인다. 
        
```
    
# 구현 코드

**[Github](https://github.com/mokhs00/CodingTest/blob/master/src/main/java/Programmers/%EC%99%84%EC%A3%BC%ED%95%98%EC%A7%80_%EB%AA%BB%ED%95%9C_%EC%84%A0%EC%88%98.java)**

``` java
import java.util.HashMap;
import java.util.Set;

class Solution {
    
    public String solution(String[] participant, String[] completion) {
        String answer = "";

        HashMap<String, Integer> map = new HashMap<>();

        for (String p : participant) {
            Integer orDefault = map.getOrDefault(p, 0);
            map.put(p, orDefault + 1);            
        }

        for (String c : completion) {
            Integer get = map.get(c);
            map.put(c, get - 1);           
        }

        Set<String> keySet = map.keySet();

        for (String key : keySet) {
            Integer count = map.get(key);
            if (count > 0) {
                answer = key;
                break;
            }

        }


        return answer;
    }
}

```
# ✔제출 결과

[제출 이미지]