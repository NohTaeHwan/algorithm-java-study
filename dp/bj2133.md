## 타일 채우기 (2133)

### 문제

3×N 크기의 벽을 2×1, 1×2 크기의 타일로 채우는 경우의 수를 구해보자.



### 입력

첫째 줄에 N(1 ≤ N ≤ 30)이 주어진다.



### 출력

첫째 줄에 경우의 수를 출력한다.



### Code

```java
import java.util.*;

public class Main {
  
    public static int [] check = new int [31];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        if(n%2 == 0)
            System.out.println(dp(n));
        else
            System.out.println(0);
    }

    public static int dp(int x){

        if(x == 0) return 1;
        if(x == 2) return 3;
        if (check[x]!=0)
            return check[x];

        int result = 3 * dp(x - 2);

        for(int i=4;i<=x;i+=2){
            result += 2 * dp(x-i);
        }
        return check[x] = result;
    }
}

```





