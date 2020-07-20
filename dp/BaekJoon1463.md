## 1로 만들기 (1463)

### 문제

정수 X에 사용할 수 있는 연산은 다음과 같이 세 가지 이다.

1. X가 3으로 나누어 떨어지면, 3으로 나눈다.
2. X가 2로 나누어 떨어지면, 2로 나눈다.
3. 1을 뺀다.

정수 N이 주어졌을 때, 위와 같은 연산 세 개를 적절히 사용해서 1을 만들려고 한다. 연산을 사용하는 횟수의 최솟값을 출력하시오.

### 입력

첫째 줄에 1보다 크거나 같고, 106보다 작거나 같은 정수 N이 주어진다.



### 출력

첫째 줄에 연산을 하는 횟수의 최솟값을 출력한다.



### Code

##### Bottom-top

```java
import java.util.*;

/**
 * bottom-top
 * 수행시간 : 136ms
 */
public class Main{

    public static int [] dp;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        dp = new int [n+1];

        dp[1] = 0;
        for(int i=2;i<dp.length;i++){

            dp[i] = dp[i-1] + 1;
            if(i%2==0) dp[i] = Math.min(dp[i],dp[i/2]+1);
            if(i%3==0) dp[i] = Math.min(dp[i],dp[i/3]+1);

        }

        System.out.print(dp[n]);
    }

}

```



##### Top-bottom

```java
import java.util.Scanner;

/**
 * Top-bottom
 * 수행시간 : 3592ms
 */
public class Main {

    public static int [] checked;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        checked = new int [n+1];

        System.out.print(dp(n));
    }

    public static int dp(int x){

        if(x==1)
            return 0;
        if(checked[x]!=0)
            return checked[x];
        else{
            checked[x] = dp(x-1) + 1;
            if(x%2==0) checked[x] = Math.min(checked[x],dp(x/2)+1);
            if(x%3==0) checked[x] = Math.min(checked[x],dp(x/3)+1);

            return checked[x];
        }

    }
}

```





