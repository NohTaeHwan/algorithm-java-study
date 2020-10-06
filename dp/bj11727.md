## 2xn 타일링 2 (11727)

### 문제

2×n 직사각형을 1×2, 2×1과 2×2 타일로 채우는 방법의 수를 구하는 프로그램을 작성하시오.

아래 그림은 2×17 직사각형을 채운 한가지 예이다.

![img](https://www.acmicpc.net/upload/images/t2n2122.gif)



### 입력

첫째 줄에 n이 주어진다. (1 ≤ n ≤ 1,000)



### 출력

첫째 줄에 2×n 크기의 직사각형을 채우는 방법의 수를 10,007로 나눈 나머지를 출력한다.



### Code

```java
import java.util.*;

public class Main {

   public static int [] tiles;

    public static int recursive(int n){

        if(n == 1) return 1;
        if(n == 2) return 3;
        if(tiles[n] != 0) return tiles[n];

        return tiles[n] = (recursive(n-1) + (2*recursive(n-2))) % 10007;

    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int length = scanner.nextInt();

        tiles = new int [length+1];

        System.out.println(recursive(length));

    }
}

```





