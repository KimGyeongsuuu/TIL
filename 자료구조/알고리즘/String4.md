# url입력
```java
package homework;

import java.util.Scanner;
public class programing04 {

	public static void main(String[] args) {
		String url;
		Scanner sc = new Scanner(System.in);
		while(true) {	
			System.out.print("URL을 입력하세요 : ");	
			url = sc.next();
			if(url.equalsIgnoreCase("bye"))
                break;
			System.out.println(url+"은 '"+finish(url)+"'으로 끝납니다.");
			System.out.println(url+"은 '"+ include(url)+"'를 포함합니다.");
		}
	}
	private static String include(String url) {
        String[] stChange1 = url.split("[.]");
		return stChange1[1];
	}

	private static String finish(String url) {
        String[] stChange1 = url.split("[.]");
		return stChange1[2];
	}

}
```