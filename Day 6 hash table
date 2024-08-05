# Day 6 hash table- 当我们遇到了要快速判断一个元素是否出现集合里的时候，就要考虑哈希法 

## 242.有效的字母异位词
Time complexity: O(n) <br>
ps: 在题目规定长度限制可以用数组解决 <br>
https://leetcode.cn/problems/valid-anagram/
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        int record[26]={0};
        for (int i=0; i<s.size(); i++){
            record[s[i]-'a']++;
        }
        for (int i=0; i<t.size(); i++){
            record[t[i]-'a']--;
        }
        for (int i=0; i<26; i++){
            if(record[i]!=0){
                return false;
            }
        }
        return true;

    }
};
``````
## 349. 两个数组的交集 
https://leetcode.cn/problems/intersection-of-two-arrays/
```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> result;
        unordered_set<int> num_set(nums1.begin(), nums1.end());
        for (int num: nums2){
            if(num_set.find(num)!=num_set.end()){
                result.insert(num);
            }
        }
        return vector<int>(result.begin(), result.end());

    }
};
``````
## 202 快乐数
https://leetcode.cn/problems/happy-number/
```cpp
class Solution {
public:
    int getSum(int n){
        int sum = 0 ;
        while (n){
            sum += (n%10)*(n%10);
            n/=10;
        }
        return sum;
    }
    bool isHappy(int n) {
        unordered_set<int> set;
        while (1){
            int sum = getSum(n);
            if(sum==1){
                return true;
            }
            if (set.find(sum)!=set.end()){
                return false;
            }
            else{
                set.insert(sum);
            }
            n=sum;
        }

    }
};
``````
## 1. 两数之和
https://leetcode.cn/problems/two-sum/ <br>
unordered_map
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> map;
        for (int i = 0; i<nums.size();i++){
            auto iter = map.find(target - nums[i]);
            if (iter != map.end()){
                return {iter->second, i};
            }
            map.insert(pair<int, int>(nums[i],i));
        }
        return {};
    }
};
``````

