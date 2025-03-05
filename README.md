[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/o-KsyuFI)
# AP-ASSIGNMENT-4-DAULAT-E13701
Sorting and Searching
https://leetcode.com/problems/merge-sorted-array/
```
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1; 
        int j = n - 1;  
        int k = m + n - 1; 
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k] = nums1[i];
                i--;
            } else {
                nums1[k] = nums2[j];
                j--;
            }
            k--;
        }
        while (j >= 0) {
            nums1[k] = nums2[j];
            j--;
            k--;
        }
    }
};

```
![image](https://github.com/user-attachments/assets/081fa2ac-9a6a-42ec-8dd2-a3bcba0cf98d)


https://leetcode.com/problems/first-bad-version/
```
class Solution {
public:
    int firstBadVersion(int n) {
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;  
            if (isBadVersion(mid)) {
                right = mid;
            } else {
                left = mid + 1; 
            }
        }
        return left; 
    }
};

```
![image](https://github.com/user-attachments/assets/2faf4953-bd97-4b1a-83fd-6a951847967b)

https://leetcode.com/problems/sort-colors/
```
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, mid = 0, high = nums.size() - 1;
        
        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums[low], nums[mid]);
                low++;
                mid++;
            } else if (nums[mid] == 1) {
                mid++;
            } else { 
                swap(nums[mid], nums[high]);
                high--;
            }
        }
    }
};

```
![image](https://github.com/user-attachments/assets/8c6f8117-8a51-4922-8f40-f0f6718b12eb)

https://leetcode.com/problems/top-k-frequent-elements/
```
#include <vector>
#include <unordered_map>
#include <queue>

using namespace std;

class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int, int> freqMap;
        for (int num : nums) {
            freqMap[num]++;
        }
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<>> minHeap;

        for (auto& [num, freq] : freqMap) {
            minHeap.push({freq, num});
            if (minHeap.size() > k) {
                minHeap.pop();  
            }
        }
        vector<int> result;
        while (!minHeap.empty()) {
            result.push_back(minHeap.top().second);
            minHeap.pop();
        }
        return result;
    }
};

```
![image](https://github.com/user-attachments/assets/e01a58f6-c73c-4877-8eed-15fad4bf518b)

https://leetcode.com/problems/kth-largest-element-in-an-array/
```
#include <vector>
#include <queue>

using namespace std;

class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        priority_queue<int, vector<int>, greater<int>> minHeap;
        
        for (int num : nums) {
            minHeap.push(num);
            if (minHeap.size() > k) {
                minHeap.pop();  
            }
        }
        
        return minHeap.top();
    }
};

```
![image](https://github.com/user-attachments/assets/69d3a09a-b527-46e6-8fc6-1723e3940e70)

https://leetcode.com/problems/find-peak-element/
```
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] > nums[mid + 1]) {
                right = mid; 
            } else {
                left = mid + 1; 
            }
        }
        
        return left;  
    }
};

```
![image](https://github.com/user-attachments/assets/f87f3294-f02b-4bc8-8be7-150750bc2d1d)

https://leetcode.com/problems/merge-intervals/
```
#include <vector>
#include <algorithm>

using namespace astd;

class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        if (intervals.empty()) return {};
        sort(intervals.begin(), intervals.end());

        vector<vector<int>> merged;
        merged.push_back(intervals[0]);
        for (int i = 1; i < intervals.size(); i++) {
            vector<int>& last = merged.back(); 

            if (intervals[i][0] <= last[1]) {
                last[1] = max(last[1], intervals[i][1]);
            } else {
                merged.push_back(intervals[i]);
            }
        }

        return merged;
    }
};

```
![image](https://github.com/user-attachments/assets/07604331-be79-46a3-9cf2-fba5885ee6ff)

https://leetcode.com/problems/search-in-rotated-sorted-array/
```
#include <vector>

using namespace std;

class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] == target) return mid;

            // Check if the left half is sorted
            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;  // Search in left half
                } else {
                    left = mid + 1;   // Search in right half
                }
            }
            // Otherwise, the right half is sorted
            else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;  // Search in right half
                } else {
                    right = mid - 1; // Search in left half
                }
            }
        }
        
        return -1; // Target not found
    }
};

```
![image](https://github.com/user-attachments/assets/02aa5460-8b6f-4584-a01b-70b9a2c705d8)

https://leetcode.com/problems/search-a-2d-matrix-ii/
```
#include <vector>

using namespace std;

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int m = matrix.size(), n = matrix[0].size();
        int row = 0, col = n - 1; // Start at top-right corner

        while (row < m && col >= 0) {
            if (matrix[row][col] == target) return true;
            else if (matrix[row][col] > target) col--; // Move left
            else row++; // Move down
        }

        return false; // Target not found
    }
};

```
![image](https://github.com/user-attachments/assets/6a4424ce-9cc6-40db-a0e5-67d9837af4c1)

https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/
```
#include <vector>

using namespace std;

class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        int n = matrix.size();
        int left = matrix[0][0], right = matrix[n-1][n-1];
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            int count = countLessEqual(matrix, mid, n);
            
            if (count < k) left = mid + 1;
            else right = mid;
        }
        
        return left;
    }
    
    int countLessEqual(vector<vector<int>>& matrix, int mid, int n) {
        int count = 0, row = n - 1, col = 0;
        
        while (row >= 0 && col < n) {
            if (matrix[row][col] <= mid) {
                count += row + 1; // All elements in this column above row are ≤ mid
                col++;
            } else {
                row--;
            }
        }
        
        return count;
    }
};

```
![image](https://github.com/user-attachments/assets/7a5a5889-fe81-47af-96d5-1ea85e2ce6b5)

https://leetcode.com/problems/median-of-two-sorted-arrays/
```
#include <vector>
#include <climits>

using namespace std;

class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        if (nums1.size() > nums2.size()) 
            return findMedianSortedArrays(nums2, nums1);          
        int m = nums1.size(), n = nums2.size();
        int left = 0, right = m, halfLen = (m + n + 1) / 2;
        
        while (left <= right) {
            int cut1 = left + (right - left) / 2;
            int cut2 = halfLen - cut1;
            
            int nums1_left = (cut1 == 0) ? INT_MIN : nums1[cut1 - 1];
            int nums1_right = (cut1 == m) ? INT_MAX : nums1[cut1];
            int nums2_left = (cut2 == 0) ? INT_MIN : nums2[cut2 - 1];
            int nums2_right = (cut2 == n) ? INT_MAX : nums2[cut2];
            
            if (nums1_left <= nums2_right && nums2_left <= nums1_right) {
                if ((m + n) % 2 == 0) 
                    return (max(nums1_left, nums2_left) + min(nums1_right, nums2_right)) / 2.0;
                else 
                    return max(nums1_left, nums2_left);
            } 
            else if (nums1_left > nums2_right) 
                right = cut1 - 1; 
            else 
                left = cut1 + 1; 
        }
        
        return 0.0;
    }
};

```
![image](https://github.com/user-attachments/assets/6718303c-29b2-48cd-ba7a-14ef5380a775)

