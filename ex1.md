가운데 글자 가져오기
==============
### 문제 설명
단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

**입력값** : 문자열(ex "abcde")

**출력값** : 문자열(ex "c")
```
function solution(s) {
    var length = s.length;
    var i;
    var answer = '';
    if ((length%2) === 0) {
        i=length/2;
        answer = s[i-1];
        answer = answer + s[i];
    } else { 
        i=parseInt(length/2);
        answer = s[i];
    }
    return answer;
}
```
* 문자열.length
  * 문자열의 길이를 반환
* 문자열중 하나의 문자열은 인덱스로 접근가능
