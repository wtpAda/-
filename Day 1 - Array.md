# Day 1 Array 

## 1. Binary Search - 204. Binary Search
Time complexity: O(log n) <br>
Application: ranked and non-duplicate array

```cpp
//204. Binary Search
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left =0;
        int right = nums.size()-1;
        
        while(left<=right){
            int mid = (left + right)/2;
            if (nums[mid]>target){
                right = mid-1;
            }
            else if (nums[mid]<target){
                left = mid+1;
            }
            else{
                return mid;
            }

        }
        return -1;

    }
};
``````
## 2. Fast and Slow Index
27. Remove element:
    old version:<br>
    Time complexity: O(n^2)<br>
    faster version:<br>
    Time complexity: O(log n)<br>
```cpp
//27. Remove element
//slower version:
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int size = nums.size();
        for (int i=0; i<size; i++){
            if (nums[i] == val){
                for (int j= i+1 ;j<size;j++){
                    nums[j-1] = nums[j];
                } 
                size--;
                i--;
            }
        }
        return size;
    }
};
``````

```cpp
//faster version:
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex<nums.size();fastIndex++){
            if (val!= nums[fastIndex]){
                nums[slowIndex] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex;
    }
};
``````
```cpp
//977. Square of sorted array
//Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        int k = nums.size()-1;
        int left = 0;
        int right = nums.size()-1;
        vector<int> result(nums.size(), 0);
        while(left<=right){
            if (nums[left]*nums[left]>=nums[right]*nums[right] ){
                result[k]=nums[left]*nums[left];
                k--;
                left++;

            }
            else if (nums[left]*nums[left]<nums[right]*nums[right]){
                result[k] = nums[right]*nums[right];
                k--;
                right--;
            }
        }
        return result;
    }
};
``````
