# [Kth Largest element in array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/) [Medium]
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

For example,  
Given `[3,2,1,5,6,4]` and k = 2, return 5.

Note:  
You may assume k is always valid, 1 ≤ k ≤ array's length.

## [Java solution](https://leetcode.com/submissions/detail/145222244/)
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length-k];
    }
}
```

## [Java solution](https://leetcode.com/submissions/detail/145228748/)
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        return quickSelect(0, nums.length-1, nums, k-1);
    }
    
    private int quickSelect(int low, int high, int[] nums, int k) {
        int pivot = nums[high];
        int i = low;
        int j = high - 1;
        
        while(i <= j) {      
            if (nums[i] < pivot) {
                swap(i, j, nums);
                j--;
                i--;
            }
            i++;
        }
        swap(i, high, nums);
        if (i == k) {
            return nums[i];
        } else if (i > k) {
            return quickSelect(low, i-1, nums, k);
        } else {
            return quickSelect(i+1, high, nums, k);
        }
        
    }
    
    void swap(int i, int j, int[] nums) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

## [Java solution](https://leetcode.com/submissions/detail/145229525/)
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        return quickSelect(0, nums.length-1, nums, k-1);
    }
    
    private int quickSelect(int low, int high, int[] nums, int k) {
        int pivot = nums[high];
        int i = low;
        int j = high - 1;
        
        while(i <= j) {      
            while (i <= j && nums[i] > pivot) {
                i++;
            }
            while (i <= j && nums[j] < pivot) {
                j--;
            }
            if (i <= j) {
                swap(i, j, nums);
                j--;
                i++;
            }
        }
        swap(i, high, nums);
        if (i == k) {
            return nums[i];
        } else if (i > k) {
            return quickSelect(low, i-1, nums, k);
        } else {
            return quickSelect(i+1, high, nums, k);
        }
        
    }
    
    void swap(int i, int j, int[] nums) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
