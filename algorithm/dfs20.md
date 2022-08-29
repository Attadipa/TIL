# 단지번호붙이기

### 백준 2667번 문제

------------

### 문제

	<그림 1>과 같이 정사각형 모양의 지도가 있다. 1은 집이 있는 곳을, 0은 집이 없는 곳을 나타낸다.
	철수는 이 지도를 가지고 연결된 집의 모임인 단지를 정의하고, 단지에 번호를 붙이려 한다.
	여기서 연결되었다는 것은 어떤 집이 좌우, 혹은 아래위로 다른 집이 있는 경우를 말한다. 
	대각선상에 집이 있는 경우는 연결된 것이 아니다. <그림 2>는 <그림 1>을 단지별로 번호를 붙인 것이다. 
	지도를 입력하여 단지수를 출력하고, 각 단지에 속하는 집의 수를 오름차순으로 정렬하여 
	출력하는 프로그램을 작성하시오.

	<img src="https://www.acmicpc.net/upload/images/ITVH9w1Gf6eCRdThfkegBUSOKd.png" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="image"></img><br/>
	
![Alt text](![Alt text](https://www.acmicpc.net/upload/images/ITVH9w1Gf6eCRdThfkegBUSOKd.png)
)


### 입력

	첫 번째 줄에는 지도의 크기 N(정사각형이므로 가로와 세로의 크기는 같으며 5≤N≤25)이 입력되고, 
	그 다음 N줄에는 각각 N개의 자료(0혹은 1)가 입력된다.

### 출력

	첫 번째 줄에는 총 단지수를 출력하시오. 
	그리고 각 단지내 집의 수를 오름차순으로 정렬하여 한 줄에 하나씩 출력하시오.


### 내 풀이

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;

public class Main {
	static int L,C;
	static char[] arr;
	static char[] answer;
	static ArrayList<Integer> sizeList = new ArrayList<>();
	
	public static void dfs(int
			lev, int start) {
		if(lev>=L) {
			int cnt = 0;
			for(char c : answer) {
				if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u') {
					cnt++;
				}
			}
			if(cnt>=1 && cnt<=L-2) System.out.println(answer);
		}
		else {
			for(int i = start ; i<C ; i++) {
				answer[lev] = arr[i];
				dfs(lev+1,i+1);
			}
		}
	}
	
    public static void main(String[] args) {
    	Scanner sc = new Scanner(System.in);
    	L = sc.nextInt();
    	C = sc.nextInt();
    	arr = new char[C];
    	answer = new char[L];
    	for(int i = 0 ; i<C ; i++) {
    		arr[i] = sc.next().charAt(0);
    	}
    	Arrays.sort(arr);
    	dfs(0,0);
    }
}
```