# [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array)

[中文文档](/solution/0000-0099/0034.Find%20First%20and%20Last%20Position%20of%20Element%20in%20Sorted%20Array/README.md)

## Description

<p>Given an array of integers <code>nums</code> sorted in non-decreasing order, find the starting and ending position of a given <code>target</code> value.</p>

<p>If <code>target</code> is not found in the array, return <code>[-1, -1]</code>.</p>

<p>You must&nbsp;write an algorithm with&nbsp;<code>O(log n)</code> runtime complexity.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [5,7,7,8,8,10], target = 8
<strong>Output:</strong> [3,4]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [5,7,7,8,8,10], target = 6
<strong>Output:</strong> [-1,-1]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [], target = 0
<strong>Output:</strong> [-1,-1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup>&nbsp;&lt;= nums[i]&nbsp;&lt;= 10<sup>9</sup></code></li>
	<li><code>nums</code> is a non-decreasing array.</li>
	<li><code>-10<sup>9</sup>&nbsp;&lt;= target&nbsp;&lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

Binary search.

Template 1:

```java
boolean check(int x) {}

int search(int left, int right) {
    while (left < right) {
        int mid = (left + right) >> 1;
        if (check(mid)) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
}
```

Template 2:

```java
boolean check(int x) {}

int search(int left, int right) {
    while (left < right) {
        int mid = (left + right + 1) >> 1;
        if (check(mid)) {
            left = mid;
        } else {
            right = mid - 1;
        }
    }
    return left;
}
```

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        l = bisect_left(nums, target)
        r = bisect_left(nums, target + 1)
        return [-1, -1] if l == len(nums) or l >= r else [l, r - 1]
```

### **Java**

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int l = search(nums, target);
        int r = search(nums, target + 1);
        return l == nums.length || l >= r ? new int[]{-1, -1} : new int[]{l, r - 1};
    }

    private int search(int[] nums, int target) {
        int left = 0, right = nums.length;
        while (left < right) {
            int mid = (left + right) >>> 1;
            if (nums[mid] >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int l = lower_bound(nums.begin(), nums.end(), target) - nums.begin();
        int r = lower_bound(nums.begin(), nums.end(), target + 1) - nums.begin();
        if (l == nums.size() || l >= r) return {-1, -1};
        return {l, r - 1};
    }
};
```

### **JavaScript**

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function (nums, target) {
    function search(target) {
        let left = 0,
            right = nums.length;
        while (left < right) {
            const mid = (left + right) >> 1;
            if (nums[mid] >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
    const l = search(target);
    const r = search(target + 1);
    return l == nums.length || l >= r ? [-1, -1] : [l, r - 1];
};
```

### **Go**

```go
func searchRange(nums []int, target int) []int {
	search := func(target int) int {
		left, right := 0, len(nums)
		for left < right {
			mid := (left + right) >> 1
			if nums[mid] >= target {
				right = mid
			} else {
				left = mid + 1
			}
		}
		return left
	}
	l, r := search(target), search(target+1)
	if l == len(nums) || l >= r {
		return []int{-1, -1}
	}
	return []int{l, r - 1}
}
```

### **Rust**

```rust
use std::cmp::Ordering;

impl Solution {
    pub fn search_range(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let n = nums.len();
        let mut l = 0;
        let mut r = n;
        while l < r {
            let mid = l + (r - l) / 2;
            match nums[mid].cmp(&target) {
                Ordering::Less => l = mid + 1,
                Ordering::Greater => r = mid,
                Ordering::Equal => {
                    let mut res = vec![mid as i32, mid as i32];
                    let mut t = mid;
                    while l < t {
                        let mid = l + (t - l) / 2;
                        match nums[mid].cmp(&target) {
                            Ordering::Less => l = mid + 1,
                            Ordering::Greater => t = mid,
                            Ordering::Equal => {
                                res[0] = mid as i32;
                                t = mid;
                            }
                        }
                    }
                    t = mid + 1;
                    while t < r {
                        let mid = t + (r - t) / 2;
                        match nums[mid].cmp(&target) {
                            Ordering::Less => t = mid + 1,
                            Ordering::Greater => r = mid,
                            Ordering::Equal => {
                                res[1] = mid as i32;
                                t = mid + 1;
                            }
                        }
                    }
                    return res;
                }
            }
        }
        vec![-1, -1]
    }
}
```

### **TypeScript**

```ts
function searchRange(nums: number[], target: number): number[] {
    function search(target) {
        let left = 0,
            right = nums.length;
        while (left < right) {
            const mid = (left + right) >> 1;
            if (nums[mid] >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
    const l = search(target);
    const r = search(target + 1);
    return l == nums.length || l >= r ? [-1, -1] : [l, r - 1];
}
```

### **...**

```

```

<!-- tabs:end -->
