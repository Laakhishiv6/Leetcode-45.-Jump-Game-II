# Leetcode-45.-Jump-Game-II
# Description
You are given a 0-indexed array of integers nums of length n. You are initially positioned at index 0.

Each element nums[i] represents the maximum length of a forward jump from index i. In other words, if you are at index i, you can jump to any index (i + j) where:

0 <= j <= nums[i] and
i + j < n
Return the minimum number of jumps to reach index n - 1. The test cases are generated such that you can reach index n - 1.
# Solution
You are given a 0-indexed array of integers nums of length n.
You start at index 0. Each element nums[i] represents the maximum length of a forward jump from index i.

That means from index i, you can jump to any index between i+1 and i+nums[i],as long as it is within bounds.

The goal is to reach the last index (n-1) in the minimum number of jumps.It is guaranteed that you can always reach the last index.
# Algorithm (Greedy approach)
1. Initialize: res = 0 → number of jumps made. l = 0, r = 0 → current window of indices we can reach with the current number of jumps.
2. While r < n - 1 (we haven’t reached the last index yet): Set farthest = 0.
3. For each index i in the range [l, r]: Update farthest = max(farthest, i + nums[i])(farthest point we can reach from this window).
4. Update the next window:l = r + 1 and r = farthest
5. Increment res by 1 (we made one jump).
6. return res.
# Code
class Solution:

    def jump(self, nums: List[int]) -> int:
        res=0
        l=r=0

        while r<len(nums)-1:
            farthest=0
            for i in range(l,r+1):
                farthest=max(farthest,i+nums[i])
            l=r+1
            r=farthest
            res+=1
        return res
# Complexity
Time Complexity: 

O(n) → Each index is visited at most once in the window loop.

Space Complexity: 

O(1) → Only variables for boundaries and jumps.
