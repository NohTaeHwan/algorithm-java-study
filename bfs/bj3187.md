## 양치기 꿍 (3187)

### 문제

양치기 꿍은 맨날 늑대가 나타났다고 마을 사람들을 속였지만 이젠 더이상 마을 사람들이 속지 않는다. 화가 난 꿍은 복수심에 불타 아예 늑대들을 양들이 있는 울타리안에 마구 집어넣어 양들을 잡아먹게 했다.

하지만 양들은 보통 양들이 아니다. 같은 울타리 영역 안의 양들의 숫자가 늑대의 숫자보다 더 많을 경우 늑대가 전부 잡아먹힌다. 물론 그 외의 경우는 양이 전부 잡아먹히겠지만 말이다.

꿍은 워낙 똑똑했기 때문에 이들의 결과는 이미 알고있다. 만약 빈 공간을 '.'(점)으로 나타내고 울타리를 '#', 늑대를 'v', 양을 'k'라고 나타낸다면 여러분은 몇 마리의 양과 늑대가 살아남을지 계산할 수 있겠는가?

단, 울타리로 막히지 않은 영역에는 양과 늑대가 없으며 양과 늑대는 대각선으로 이동할 수 없다.

### 입력

입력의 첫 번째 줄에는 각각 영역의 세로와 가로의 길이를 나타내는 두 개의 정수 R, C (3 ≤ R, C ≤ 250)가 주어진다.

다음 각 R줄에는 C개의 문자가 주어지며 이들은 위에서 설명한 기호들이다.



### 출력

살아남게 되는 양과 늑대의 수를 각각 순서대로 출력한다.



### Code

```java
import java.util.*;

/**
 * 수행시간 : 184ms
 */
public class Main {

    public static char [][] farm;
    public static boolean [][] visited;
    public static int R;
    public static int C;
    public static int wolf = 0;
    public static int sheep = 0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        R = scanner.nextInt();
        C = scanner.nextInt();

        farm = new char[R][C];
        visited = new boolean[R][C];

        for(int i=0;i<R;i++)
            farm[i] = scanner.next().toCharArray();

        for(int i=0;i<R;i++){
            for(int j=0;j<C;j++){
                if(farm[i][j]=='v'||farm[i][j]=='k'){
                    bfs(i,j);
                }

            }
        }

        System.out.println(sheep+" "+wolf);

    }

    public static void bfs(int row, int col){
        LinkedList<Point> queue = new LinkedList<>();
        queue.add(new Point(row,col));
        visited[row][col] = true;
        int wolfCount = 0, sheepCount = 0;

        while (!queue.isEmpty()){
            Point p = queue.poll();
            int r = p.getRow();
            int c = p.getCol();

            //늑대 , 양 체크
            if(farm[r][c]=='v')
                wolfCount++;
            else if(farm[r][c]=='k')
                sheepCount++;

            farm[r][c] = '#';

            //상
            if((r-1)>=0 && farm[r-1][c]!='#' && !visited[r-1][c]){
                visited[r-1][c] = true;
                queue.add(new Point(r-1,c));
            }

            //하
            if((r+1)<=(R-1) && farm[r+1][c]!='#' && !visited[r+1][c]){
                visited[r+1][c] = true;
                queue.add(new Point(r+1,c));
            }

            //좌
            if((c-1)>=0 && farm[r][c-1]!='#' && !visited[r][c-1]){
                visited[r][c-1] = true;
                queue.add(new Point(r,c-1));
            }

            //우
            if((c+1)<=(C-1) && farm[r][c+1]!='#' && !visited[r][c+1]){
                visited[r][c+1] = true;
                queue.add(new Point(r,c+1));
            }

        }

        if(wolfCount>=sheepCount)
            wolf += wolfCount;
        else
            sheep += sheepCount;
    }
}

class Point{
    int row;
    int col;

    public Point(int row,int col){
        this.row = row;
        this.col = col;
    }

    public int getRow(){
        return row;
    }

    public int getCol(){
        return col;
    }
}
```

