# Day 2 Array advanced

## 1. sliding window 滑动窗口
209. min size subarray sum<br>
Time complexity: O(n) <br>
https://leetcode.cn/problems/minimum-size-subarray-sum/<br>
可以将原本O(N^2)降低为）O(N), for 遍历窗口末端index， 同时不断更新窗口初始位置Index, 每个元素一进一出两次操作<br>
主要不要打乱原始数组顺序<br>

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
59. Spiral matrix 2<br>
Time complexity: O(n^2) <br>
主要是要按顺序进行模拟，以及注意边界（左闭右开）<br>
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
也可以说是前缀和， 通过cum_sum 避免O(N^2)<br>
时间复杂度： O(N) <br>
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
## 房地产问题 （***）
也是用区间和法，将原本时间复杂度由O(N^3), 简化到O(N^2), 整体流程稍复杂，需要多看<br>
https://kamacoder.com/problempage.php?pid=1044
```cpp
#include <iostream>
#include <climits>
#include <vector>
using namespace std;
int main(){
    int n, m;
    cin>> n >> m;
    vector<vector<int>> vec(n, vector<int>(m,0));
    int sum=0;
    for (int i = 0; i<n; i++){
        for (int j=0; j<m; j++){
            cin >> vec[i][j];
            sum += vec[i][j];
        }
    }
    
    vector<int> horizontal(n, 0);
    for (int i = 0; i < n; i++) {
        for (int j = 0 ; j < m; j++) {
            horizontal[i] += vec[i][j];
        }
    }
    // 统计纵向
    vector<int> vertical(m , 0);
    for (int j = 0; j < m; j++) {
        for (int i = 0 ; i < n; i++) {
            vertical[j] += vec[i][j];
        }
    }
    int result = INT_MAX;
    int horizontal_cut = 0;
    int vertical_cut = 0;
    for (int i = 0; i<n; i++){
        horizontal_cut+=horizontal[i];
        result = min(result, abs(sum-horizontal_cut*2));
    }
    for (int j = 0; j<m; j++){
        vertical_cut+=vertical[j];
        result = min(result, abs(sum-vertical_cut*2));
    }
    cout << result << endl;
     
}
``````
