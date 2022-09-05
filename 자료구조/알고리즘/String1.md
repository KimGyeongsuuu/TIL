# 문자열에 포함된 문자의 개수 반환
1. String char countChar(String s , char c) 메서드가 있다.
2. s 에 포함된 c의 개수를 반환해라.
```java
package homework;

public class programing01 {

	public static void main(String[] args) {
		String s = "chickccen";
		System.out.println(countChar(s,'c'));
		
	}
	static int countChar(String s, char c) {
		int count = 0;
		for(int i=0;i<s.length();i++) {
			if(s.charAt(i)==c) {
				count++;
			}
		}
		return count;
	}

}
```