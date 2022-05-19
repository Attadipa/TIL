# 선택정렬(Selection Sort)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

1. 내 풀이는 최소값인 요소를 지워가는 방식으로 풀이했다.
2. 요소끼리의 교환방식이 정석이다.

```java
public class Main {
	public static String Solution(int n, int[] arr) {
		ArrayList<Integer> list = new ArrayList<>();
		for(int i : arr) list.add(i);
		String answer = "";
		
		while(list.size()>0) {
			int min = list.get(0);
			int idx = 0;
			for(int i=1 ; i<list.size() ; i++) {
				if(min>list.get(i)) {
					min=list.get(i);
					idx=i;
				}
			}
			answer+=min+" ";
			list.remove(idx);
		}
		return answer;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(n,arr));
	} 
}
```
