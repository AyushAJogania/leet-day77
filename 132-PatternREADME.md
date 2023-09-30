# leet-day77

# 132 Pattern

## Problem Description

Given an array of integers `nums`, a "132 pattern" is a subsequence of three integers `nums[i]`, `nums[j]`, and `nums[k]` such that `i < j < k` and `nums[i] < nums[k] < nums[j]`.

Write a C++ function, `find132pattern`, that takes an integer vector `nums` and returns `true` if there exists a "132 pattern" in the sequence, and `false` otherwise.

## Example

**Input**:
```cpp
std::vector<int> nums = {1, 2, 3, 4};
```
**Output**:
```
false
```
**Explanation**:
There is no "132 pattern" in the sequence.

**Input**:
```cpp
std::vector<int> nums = {3, 1, 4, 2};
```
**Output**:
```
true
```
**Explanation**:
There is a "132 pattern" in the sequence: [1, 4, 2].

## Constraints

- The length of `nums` is between 1 and 2 * 10^5.
- The values of `nums[i]` are between -10^9 and 10^9.

## Approach

We can solve this problem using a stack and some auxiliary data structures. Here's an overview of the approach:

1. Create a vector `minPrefix` to store the minimum element up to the current index. Initialize it with the first element of `nums`.

2. Iterate through the `nums` array to fill the `minPrefix` array with the minimum element encountered so far.

3. Use a stack to keep track of potential candidates for the `2` in the "132 pattern." We iterate through the `nums` array from right to left.

4. For each element `nums[j]`, check if it's greater than the minimum element before it (`minPrefix[j]`). If it is, start popping elements from the stack that are less than or equal to `minPrefix[j]`. These elements can't be the `2` in the pattern.

5. If you find an element on the stack that's less than `nums[j]`, it means you've found a valid "132 pattern," so return `true`.

6. If you don't find a valid pattern after iterating through the entire array, return `false`.

## Complexity Analysis

- Time Complexity: O(n), where n is the length of the `nums` array.
- Space Complexity: O(n) due to the stack and `minPrefix` array.

## How to Use

To use this function, follow these steps:

1. Include the necessary header files at the beginning of your C++ file:

```cpp
#include <vector>
#include <stack>
```

2. Copy and paste the `find132pattern` function into your C++ file.

3. Create a vector of integers, `nums`, and populate it with your input data.

4. Call the `find132pattern` function with `nums` as the argument to check for the "132 pattern."

5. The function will return `true` if a "132 pattern" exists in the input sequence; otherwise, it will return `false`.

Here's an example of how to use the `find132pattern` function:

```cpp
#include <iostream>
#include <vector>
#include <stack>

// ... (Copy and paste the find132pattern function here)

int main() {
    std::vector<int> nums = {3, 1, 4, 2};
    bool hasPattern = find132pattern(nums);
    
    if (hasPattern) {
        std::cout << "The sequence contains a 132 pattern." << std::endl;
    } else {
        std::cout << "No 132 pattern found in the sequence." << std::endl;
    }
    
    return 0;
}
