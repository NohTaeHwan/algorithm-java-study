## 소수 구하기(summer/winter coding)

### 문제

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
- nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.

### Code

```java
class Solution {
    public int solution(int[] nums) {

        Selector selc = new Selector(nums);
        selc.combination(3,0,0);
        
        return selc.sum;
    }

    //combination
    class Selector {

        int n;//조합에 사용될 수의 갯수
        int [] countArr;
        int [] nums;
        int sum;

        public Selector(int [] nums){

            this.nums = nums;
            countArr = new int [nums.length];
            n = nums.length;
            sum = 0;
        }

        public void combination(int r, int idx , int tar){

            if(r==0){
                int temp = 0;
                boolean isPrime = true;

                for(int i=0;i<idx;i++){
                    temp += nums[countArr[i]];
                }
                for(int i=2;i<temp;i++){
                    if(temp%i==0){
                        isPrime = false;
                        break;
                    }
                }
                if(isPrime)
                    sum++;

            }else if(tar == n) return;
            else{
                countArr[idx] = tar;
                combination(r-1,idx+1,tar+1);
                combination(r,idx,tar+1);
            }
        }
    }
}
```

