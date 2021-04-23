완주하지 못한 선수 (HASH)
---------------

Ans

~~~~~~~java

import java.util.*; 

class Solution { 
  public String solution(String[] participant, String[] completion) { 

    String answer = ""; 

    Arrays.sort(participant); 
    Arrays.sort(completion); 

    int i; 

        for(i = 0; i < completion.length; i++){ 
            if(!participant[i].equals(completion[i])){ 
            
             return participant[i]; 
            
            } 
            
        } 
            
            return participant[i]; 

  } 
}

~~~~~~~

### Keyword
~~~~~~~java
//import해서 쓰고싶은 클래스메소드를 쓰기 위해 선언한다
import java.util.*; 


//Sort는 알파벳은 abc..순서대로, 숫자는 1,2,3.. 순서대로 정렬해준다

//Array.sort
//Sort하고싶은 배열을 아래처럼 사용
Arrays.sort(participant);


// A sample Java program to sort an array of integers
// using Arrays.sort(). It by default sorts in
// ascending order
import java.util.Arrays;
 
public class SortExample
{
    public static void main(String[] args)
    {
        // Our arr contains 8 elements
        int[] arr = {13, 7, 6, 45, 21, 9, 101, 102};
 
        Arrays.sort(arr);
 
        System.out.printf("Modified arr[] : %s",
                          Arrays.toString(arr));
    }
}

//Output

Modified arr[] : [6, 7, 9, 13, 21, 45, 101, 102]




// for문에서 : 의 의미

for (Object obj : files)

for(DrawObject obj : list)

...

for( A : B )

B에 0, 1, 2, 3, 4, 5 의 값이 들어가있을 때

A = 0;
A = 1;
A = 2;
A = 3;
A = 4;
A = 5;

~~~~~~~

Ans - HASH를 이용한 풀이(Key & Value)

> getOrDefault() -> 찾는 키가 존재하면 해당 키의 값을 반환하고, 없으면 기본값을 반환함.
hash.getOrDefault(arg라는 키, arg키가 존재하면 해당 값/없으면 0) 그리고 +1
완주한 선수 completion을 map에 추가할 때 1씩 빼주고, 해당하는 키 값이 0이 아닐 때 완주하지 못한 선수이므로
해당 key를 return하여 출력


~~~java
import java.util.*; 

class Solution { 
  public String solution(String[] participant, String[] completion) { 
    
    Map<String, Integer> hash = new HashMap<>(); 
    
    for (String arg : participant){ 

      hash.put(arg, hash.getOrDefault(arg, 0) + 1); 

      } 

      for (String arg : completion){ 

        hash.put(arg, hash.get(arg) - 1); 

        } 
        
        for (String key : hash.keySet()) { 

          if (hash.get(key) != 0){ 
            
            return key; 
            } 
          } 
            return null; 
    } 
}
~~~

### Keyword

HashMap
----
![hashmap](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcfpMTT%2FbtqEvxLt6qb%2FMXYNWUvXCKfRvNWjDMZoq0%2Fimg.png)
[HashMap](https://coding-factory.tistory.com/556)

~~~~~~~java
//HashMap 선언 및 값추가, 출력

HashMap<Integer,String> map = new HashMap<>();//new에서 타입 파라미터 생략가능
map.put(1,"사과"); //값 추가
map.put(2,"바나나");
map.put(3,"포도");

System.out.println(map); //전체 출력 : {1=사과, 2=바나나, 3=포도}
System.out.println(map.get(1));//key값 1의 value얻기 : 사과








~~~~~~~


K번째 수 (정렬)
---------------
Ans
~~~~~~~~~~~~~~~~~~~~java
import java.util.Arrays; 


class Solution { 
  public int[] solution(int[] array, int[][] commands) { 

    int[] array = {1, 5, 2, 6, 3, 7, 4};
    int[][] commands = {{2, 5, 3}, {4, 4, 1}, {1, 7, 3}};

    int[] answer = new int[commands.length]; 
    
        for(int i=0; i<commands.length; i++){ 

        int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]); 
        
        Arrays.sort(temp); 
        
        answer[i] = temp[commands[i][2]-1]; 
        
        } 

      return answer; 
   } 
      
}

~~~~~~~~~~~~~~~~~~~~


### Keyword

~~~java
//JAVA 특정범위 배열복사 

Arrays.copyOfRange

//사용방법

Arrays.copyOfRange(배열, 시작인덱스, 끝인덱스)

//결과물

arr의 요소 중 인덱스2에서 5까지  불러오기 : 2,3,4,5 

//예제 코드

import java.util.*;

public class Solution {
private static int[] arr = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

public static void main(String[] args) {

//여기서 Arrays.copyOfRange 실행
int[] arr1 = Arrays.copyOfRange(arr, 2,6);

System.out.print("arr의 요소 중 인덱스2에서 5까지  불러오기 :  ");
for(int i=0;i<arr1.length;i++) {
System.out.print(arr1[i]+" ");
    }
  }
}


~~~