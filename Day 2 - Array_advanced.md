# Day 2 Array advanced

## 1. sliding window 滑动窗口
209. min size subarray sum<br>
Time complexity: O(n) <br>
https://leetcode.cn/problems/minimum-size-subarray-sum/

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int result = INT32_MAX;
        int sum = 0;
        int i = 0;
        int sublength = 0;

        for (int j = 0; j<nums.size();j++){
            sum+=nums[j];
            while(sum>=target){
                sublength = j-i+1;
                result = result < sublength? result: sublength;
                sum-=nums[i];
                i++;
            }
        }
        if (result <INT32_MAX) return result;
        else return 0;

    }
};
``````
## 2. process monitoring - 模拟过程
59. Spiral matrix 2
Time complexity: O(n^2) <br>
https://leetcode.cn/problems/spiral-matrix-ii/
```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n, vector<int>(n,0));
        int startx = 0;
        int starty = 0;
        int count =1;
        int loop = n/2;
        int i,j;
        int offset = 1;
        int mid = n/2;

        while (loop--){
            i=startx;
            j=starty;
            for (j; j<n-offset;j++){
                res[i][j] = count;
                count++;
            }
            for (i;i<n-offset;i++){
                res[i][j] = count++;
            }
            for (j;j>starty;j--){
                res[i][j] = count++;
            }
            for (i;i>startx;i--){
                res[i][j] = count++;
            }
            startx++;
            starty++;
            offset++;
        } 
        if (n%2!=0){
                res[mid][mid] = (n*n);
            }
        return res;
    }
};
``````
## 3. 区间和
https://kamacoder.com/problempage.php?pid=1070
```cpp
#include <iostream>
#include <vector>
using namespace std;
int main(){
    int n, a, b;
    cin>>n;
    vector<int> arr(n);
    vector<int> p(n);
    int presum=0;
    for (int i=0; i<n;i++){
        cin>>arr[i];
        presum+=arr[i];
        p[i] = presum;
        
    }
    while (cin>>a>>b){
        int sum;
        if (a==0) sum=p[b];
        else{
        sum = p[b]-p[a-1];}
        cout<< sum<<endl;
        
    }
    
}
``````
