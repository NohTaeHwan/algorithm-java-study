## NHN Pre-Test 1 차 기출문제



### 문제

모든 원소가 0 또는 1 인 행렬이 있습니다. 1 로 표시된 원소는 영역을 나타냅니다. 여기에서 상하좌우에 인접한 1 은 같은 영역이라고 가정합니다. 각 영역의 크기는 1 의 개수로 정의합니다. 주어진 N x N 크기의 행렬에서 영역의 개수와 각 영역의 크기를 오름차순으로 출력하세요.

### 입력

• 첫 번째 행은 행렬의 크기인 N입니다. N 은 1 이상 10 이하의 자연수입니다. • 입력 두 번째 행부터는 공백으로 구분된 0 과 1 로 행렬이 주어집니다. 각 행은 개행 문자(newline, \n)로 구분됩니다.

### 출력

- 첫 번째 행은 영역의 개수를 출력합니다. 
- 두 번째 행은 각 영역의 크기를 공백으로 구분하여 오름차순으로 출력합니다. 
- 한 행의 끝은 불필요한 공백 없이 개행 문자(newline, \n)로 끝나야 합니다. 
- 영역이 존재하지 않을 경우 영역 수 0으로 1 행으로만 출력합니다.



### Code

```java

import java.util.*;

public class NHNPretest1 {

    public static int [][] map;

    //방향 동서남북
    public static int [] dx = {0,-1,0,1};
    public static int [] dy = {1,0,-1,0};

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> answer = new ArrayList<>();

        int n = scanner.nextInt();
        map = new int [n][n];

        for(int i=0;i<n;i++){

            for(int j=0;j<n;j++){
                map[i][j] = scanner.nextInt();
            }

        }


        for(int i=0;i<n;i++){

            for(int j=0;j<n;j++){

                if(map[i][j] != 0){
                    int result = bfs(i,j);
                    answer.add(result);
                }
            }
        }

        Collections.sort(answer);
        System.out.println(answer.size());
        for(int element : answer){
            System.out.print(element + " ");
        }


    }

    public static int bfs(int x,int y){

        int count = 1;
        Queue<Point1> queue = new LinkedList<>();
        queue.offer(new Point1(x,y));
        map[x][y] = 0;

        while(!queue.isEmpty()){

            Point1 p = queue.poll();

            for(int i=0;i<4;i++){
                int nx = p.x + dx[i];
                int ny = p.y + dy[i];

                if(check(nx,ny)){
                    continue;
                }
                if(map[nx][ny] == 1){
                    queue.offer(new Point1(nx,ny));
                    map[nx][ny] = 0;
                    count++;
                }
            }
        }

        return count;
    }

    public static boolean check(int nx,int ny){

        if(nx<0||nx==map.length||ny<0||ny==map.length)
            return true;
        return false;
    }


}

class Point1{
    int x;
    int y;

    public Point1(int row,int col){
        this.x = row;
        this.y = col;
    }

}

```



reference 

> https://recruit.nhn.com/pdf/%ED%94%84%EB%A6%AC%ED%85%8C%EC%8A%A4%ED%8A%B8_1%EC%B0%A8_%EA%B8%B0%EC%B6%9C%EB%AC%B8%EC%A0%9C.pdf