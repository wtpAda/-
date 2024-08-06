# Day7 hashtable2

## 15 3 sum 
slow and fast index is faster than hash<br>
https://leetcode.cn/problems/3sum/description/
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> result;
        for (int i=0; i<nums.size(); i++){
            if (nums[i]>0) {
                return result;
            }
            if (i>0 && nums[i]==nums[i-1]){
                continue;
            }
            int left = i+1;
            int right = nums.size()-1;
            while (right >left){
                if (nums[i]+nums[left]+nums[right]>0) right--;
                else if (nums[i]+nums[left]+nums[right]<0 ) left++;
                else{
                    result.push_back(vector<int>{nums[i], nums[left], nums[right]});
                    while(right>left && nums[right]==nums[right-1]) right--;
                    while(right>left && nums[left]==nums[left+1]) left++;
                    right--;
                    left++;
                }
            }
            
        }return result;
    }
};
``````
## 383 ransom letter
array<br>
https://leetcode.cn/problems/ransom-note/submissions/552900954/
```cpp
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        int record[26]={0};
        if (magazine.size() < ransomNote.size()){
            return false;
        }
        for (int i=0; i<magazine.length(); i++){
            record[magazine[i] - 'a']++;

        }
        for (int j=0; j<ransomNote.length(); j++){
            record[ransomNote[j]-'a']--;
            if (record[ransomNote[j]-'a']<0){
                return false;
            }
        }

        return true;


    }
};
``````
## 454 4 sum2
[https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.cn/problems/4sum-ii/submissions/552893168/)
```cpp
class Solution {
public:
    int fourSumCount(vector<int>& nums1, vector<int>& nums2, vector<int>& nums3, vector<int>& nums4) {
        unordered_map<int, int> map;
        for (int a : nums1){
            for (int b: nums2){
                map[a+b]++;

            }
        }
        int cnt=0;
        for (int c: nums3){
            for (int d: nums4){
                if (map.find(0-(c+d))!= map.end()){
                    cnt+=map[0-(c+d)];
                }
            }
        }
        return cnt;

    }
};
``````

