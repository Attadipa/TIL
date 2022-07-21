# 공통원소 구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (ArraysList에 담아서 sort)

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {
    public static void  solution(int n, int m, int[] arr1, int[] arr2) { 
    	ArrayList<Integer> list = new ArrayList<>();
    	for(int i = 0 ; i<n ; i++) {
        	for(int j = 0 ; j<m ; j++) {
        		if(arr1[i]==arr2[j]) list.add(arr1[i]);
            }
        }
    	Collections.sort(list);
    	for(int i : list) System.out.print(i+" ");	
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr1 = new int[n];
        for(int i = 0 ; i<n ; i++) {
        	arr1[i] = sc.nextInt();
        }
        int m = sc.nextInt();
        int[] arr2 = new int[m];
        for(int i = 0 ; i<m ; i++) {
        	arr2[i] = sc.nextInt();
        }
        solution(n,m,arr1,arr2);
    }
}
```

풀이2(two pointers이용)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static String solution(int n, int m, int[] arr1, int[] arr2) { 
    	int p1 = 0;
    	int p2 = 0;
    	String answer = "";
    	while(p1<n && p2<m) {
    		if(arr1[p1]<arr2[p2]) p1++;
    		else if(arr1[p1]>arr2[p2]) p2++;
    		else {
    			answer += arr1[p1]+" ";
    			p1++;
    			p2++;
    		}
    	}
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr1 = new int[n];
        for(int i = 0 ; i<n ; i++) {
        	arr1[i] = sc.nextInt();
        }
        Arrays.sort(arr1);
        int m = sc.nextInt();
        int[] arr2 = new int[m];
        for(int i = 0 ; i<m ; i++) {
        	arr2[i] = sc.nextInt();
        }
        Arrays.sort(arr2);
        System.out.println(solution(n,m,arr1,arr2));
    }
}
```