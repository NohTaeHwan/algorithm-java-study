## 정수 삼각형 (1932)

### 문제

- ```
          7
        3   8
      8   1   0
    2   7   4   4
  4   5   2   6   5
  ```

  위 그림은 크기가 5인 정수 삼각형의 한 모습이다.

  맨 위층 7부터 시작해서 아래에 있는 수 중 하나를 선택하여 아래층으로 내려올 때, 이제까지 선택된 수의 합이 최대가 되는 경로를 구하는 프로그램을 작성하라. 아래층에 있는 수는 현재 층에서 선택된 수의 대각선 왼쪽 또는 대각선 오른쪽에 있는 것 중에서만 선택할 수 있다.

  삼각형의 크기는 1 이상 500 이하이다. 삼각형을 이루고 있는 각 수는 모두 정수이며, 범위는 0 이상 9999 이하이다.



### 입력

첫째 줄에 삼각형의 크기 n(1 ≤ n ≤ 500)이 주어지고, 둘째 줄부터 n+1번째 줄까지 정수 삼각형이 주어진다.



### 출력

첫째 줄에 합이 최대가 되는 경로에 있는 수의 합을 출력한다.



### Code

##### 

```java
import java.util.*;

/**
 * bottom-top
 * 수행시간 : 776ms
 */
public class Main {

    public static int [][] tri;
    public static int [][] dp;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        tri = new int [n][];
        dp = new int [n][];

        for(int i=0;i<n;i++){

            tri[i] = new int [i+1];
            dp[i] = new int [i+1];
            for(int j=0;j<=i;j++){
                tri[i][j] = scanner.nextInt();
            }

        }

        dp[0][0] = tri[0][0];

        for(int i=1;i<n;i++){

            for(int j=0;j<=i;j++){
                if(j==0) dp[i][j] = tri[i][j] + dp[i-1][j];

                else if(j==i) dp[i][j] = tri[i][j] + dp[i-1][j-1];

                else dp[i][j] = tri[i][j] + Math.max(dp[i-1][j-1],dp[i-1][j]);
            }
        }
        int max = dp[n-1][0];

        for(int i=1;i<dp[n-1].length;i++){
            max = Math.max(max,dp[n-1][i]);
        }
        System.out.print(max);
    }
}
```



