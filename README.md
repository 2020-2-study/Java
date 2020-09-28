# 프로그래밍 응용2(Java)

## 7강 제니릭과 컬렉션

##### 2020.09.21

> ##### `stack<Interger> s = new Stack<Integer>; `
> + 컬렉션에는 객체만 저장될 수 있기 때문에 기본적인 데이터 타입 **int**와 같은 경우는 불가능하다. 따라서 <Integer>와 같이 입력한다.

> + ###### peek() : 스택에서 제일 위인 top을 리턴
> + ###### empty() : 스택이 비어있는지 test 한다. 만약 비어있으면 true, 비어있지 않으면 false를 return한다.
> + ###### search() : 인덱스 값을 리턴 만약 들어있지 않는 값을 입력하면 -1이 리턴된다.	

``` 	
import java.util.*;
public class StackTest
{
    public static void main(String[] args){
        Stack<Integer> s = new Stack<Integer>();
        s.push(921);
        s.push(2020);
        s.push(11);

        System.out.println("pop: " + s.pop());
        
        System.out.println("peek: " + s.peek());
        System.out.println("empty: " + s.empty());
        System.out.println("search(2020) : "+ s.search(2020));
        System.out.println("search(11) : " + s.search(11));
    }
}
```

![출력화면](https://user-images.githubusercontent.com/63287630/94412508-d38e6e00-01b4-11eb-812a-d1b75a150943.png)

> + **ArrayList< E >**
> + < > 안에는 객체만 저장할 수 있기 때문에 원하는 클래스의 이름을 넣어야 한다. 
> 	+ 말 그대로 배열과 비슷하지만 크기가 **가변적(마음대로 변경 가능)**이기 때문에 배열보다 좋다.
> 	+ **객체만 저장가능**
> 	+ 일반적인 숫자와 같은 것은 저장할 수 없다. 하지만 숫자 같은 경우는(기본타입) 박싱/언박싱으로 Wrapper와 객체로 만들어 저장
> 	+ **장점**
> 		1. 리스트의 맨 뒤에 객체 추가
> 		2. 리스트의 중간에 객체 삽입
> 		3. 임의의 위치에 있는 객체 삭제 가능
> 		-> 마음대로 추가, 삽입, 삭제가 가능  
>
>
>  
>  + **문자열이 저장되는 ArrayList**
>  	+ ##### `ArrayList<String> al = new ArrayList<String>();`
>  		+ ###### add() : 요소 저장(삽입)하는 메소드
>  		+ ###### get() : 저장되어있는 것을 가져오는 메소드
>  		+ ###### remove() : 요소 삭제
>  		+ ###### size() : ArrayList 안에 들어있는 요소들의 개수를 알려주는 메소드



> + **iterator() 인터페이스**
> 	+ 어떠한 컬렉션에도 적용이 됨.
> 	+ 컬렉션은 많은 요소들이 저장되어 있고 그런 요소들마다 반복적인 처리를 하는 일들이 많아서 좀 더 편리하게 하기 위해 만듦
> 	+ ###### next() : 요소 하나씩 가져오는 메소드
> 	+ ###### hasNext() : 다음번에 요소가 들어있는지 여불르 알려준느 메소드 있으면 True로 없으면 False

```
import java.util.*;
public class ArrayTest
{
    public static void main(String[] args){
        ArrayList<String> al = new ArrayList<String>(); 
        
        al.add("SunMoon");
        al.add("GSE");
        al.add("강다빈");
        
        // System.out.println(al.get(0));
        // System.out.println(al.get(1));
        // System.out.println(al.remove(0));
        // System.out.println(al.get(0));
        
        for(int i = 0; i < al.size() ; i++){
            System.out.println(al.get(i));
        }

        Iterator<String> it = al.iterator(); 
        while(it.hasNext()){
            String x = it.next();
            System.out.println(x);      
        }
    }
}
```

![출력화면](https://user-images.githubusercontent.com/63287630/94413363-f1100780-01b5-11eb-901d-140657142e29.png)


##### 2020.09.23
+ Collection 클래스
	+ 모든 메소드는 static 타입
	+ 주요 메소드
		+ ###### sort() : 컬랙션에 포함된 요소들을 소팅
		+ ###### reverse() : 요소의 순서를 반대로 함
		+ ###### max(), mini() : 요소들의 최대, 최솟값을 찾아냄 
		+ ###### binaryserach(): 특정 값을 검색
			+ => Collectios.sort() , Collections.reverse()  

```
public class GStack<T> 
{
    private int top;
    Object[] s; 
    
    public GStack(){
        top = -1;
        s = new Object[6];
    }

    public void push(T data){
        top += 1;
        s[top] = data;
    }    
    
    public T pop(){
        T result = (T)s[top];
        top -= 1;
        return result;
    }
}
```
