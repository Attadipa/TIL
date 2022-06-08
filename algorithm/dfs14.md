# 조합구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


내 풀이1(순열 만들고 중복제거. 보기만 해도 마음이 무거워진다.)

```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
	
	static int n,m;
	static int[] arr, check;
	static ArrayList<ArrayList<Integer>> result = new ArrayList<>();

	public static void dfs(int lev) {
		if(lev==m) {
			ArrayList<Integer> list = new ArrayList<>();
			for(int i : arr) list.add(i);
			result.add(list);
		}
		else {
			for(int i =1 ; i<=n ; i++) {
				if(check[i]==0) {
					check[i]=1;
					arr[lev]=i;
					dfs(lev+1);
					check[i]=0;
				}
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new int[m];
		check = new int[n+1];
		dfs(0);
		int[] checkResult = new int[result.size()];
		for(int i = 0 ; i < result.size() ; i++) {
			for(int j = i+1 ; j<result.size() ; j++) {
				if(result.get(i).containsAll(result.get(j))){
					checkResult[j]=1;
				}
			}
			if(checkResult[i]==0) {
				for(int in : result.get(i)) {
					System.out.print(in+" ");
				}
				System.out.println();
			}
		}
	}
} 
```

내 풀이2(부분집합 구하는 로직에서 부분집합 크기만 제한)

```java
import java.util.Scanner;

public class Main {
	
	static int n,m;
	static int[] arr;

	public static void dfs(int lev, int cnt) {
		if(cnt==m) {
			for(int i : arr) System.out.print(i+" ");
			System.out.println();
			return;
		}
		if(lev==n) return;
		else {
			arr[cnt] = lev+1;
			dfs(lev+1, cnt+1);
			dfs(lev+1, cnt);
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new int[m];
		dfs(0,0);
	}
} 
```

해설(뻗어나가는 가짓수 제한)

```java
import java.util.Scanner;

public class Main {
	
	static int n,m;
	static int[] combi;

	public static void dfs(int lev, int s) {
		if(lev==m){
			for(int i : combi) System.out.print(i+" ");
			System.out.println();
		} else {
			for(int i = s ; i<=n ; i++) {
				combi[lev]=i;
				dfs(lev+1,i+1);
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		combi = new int[m];
		dfs(0,1);
	}
} 
```