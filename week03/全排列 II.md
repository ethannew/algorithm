~~~c++
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> path;
    vector<bool> st;

    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        path = vector<int>(nums.size());
        st = vector<bool>(nums.size());
        dfs(nums, 0);
        return ans;
    }

    void dfs(vector<int>&nums, int u) {
        if (u == nums.size()) {
            ans.push_back(path);
            return;
        }

        for (int i = 0; i < nums.size(); i ++ ) {
            if (!st[i]) {
                if (i && nums[i - 1] == nums[i] && !st[i - 1]) continue;
                st[i] = true;
                path[u] = nums[i];
                dfs(nums, u + 1);
                st[i] = false;
            }
        }
    }
};
~~~

时间复杂度O(N!)，空间复杂度O(N)