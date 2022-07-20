# 두 배열 합치기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (ArraysList에 담아서 sort)

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
    	ArrayList<Integer> list = new ArrayList<>();
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] narr = new int[n];
        for(int i = 0 ; i<n; i++) {
            list.add(sc.nextInt());
        }
        int m = sc.nextInt();
        int[] marr = new int[m];
        for(int i = 0 ; i<m; i++) {
            list.add(sc.nextInt());
        }
        Collections.sort(list);
        for(int i : list) System.out.print(i + " ");
    }
}
```

풀이2(two pointers 이용)
```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    public static String solution(int n, int m, int[] arr1, int[] arr2) {
    	ArrayList<Integer> list= new ArrayList<Integer>();
    	int p1 = 0, p2 = 0;
    	while(p1<n && p2<m) {
    		if(arr1[p1]<=arr2[p2]) list.add(arr1[p1++]);
    		else list.add(arr2[p2++]);
    	}
    	while(p1<n) list.add(arr1[p1++]);
    	while(p2<m) list.add(arr2[p2++]);
    	
    	String answer = "";
    	for(int i : list) {
    		answer += i+" ";
    	}
        return answer;
    }
    public static void main(String[] args) {
    	ArrayList<Integer> list = new ArrayList<>();
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr1 = new int[n];
        for(int i = 0 ; i<n; i++) {
        	arr1[i] = sc.nextInt();
        }
        int m = sc.nextInt();
        int[] arr2 = new int[m];
        for(int i = 0 ; i<m; i++) {
        	arr2[i] = sc.nextInt();
        }
        System.out.println(solution(n,m,arr1,arr2));
    }
}
```