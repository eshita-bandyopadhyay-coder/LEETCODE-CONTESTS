// LEETCODE CONTEST 419 Q1
class Solution {
public:
    vector<int> findXSum(vector<int>& nums, int k, int x) {
       int n=nums.size();
       vector <int>ans(n-k+1);
       for(int i=0; i<n-k+1; i++)
       {
        map<int, int> cnt;
        for(int j=i;j<i+k;j++)
        {
            cnt[nums[j]]++;
        }
        vector<pair<int,int>>a;
        for(auto it:cnt)
        {
            a.push_back({it.second,it.first});
        }
        sort(a.begin(),a.end(),greater<pair<int,int>>());
        for(int j=0;j<a.size() && j<x; j++)
        {
            ans[i]=ans[i]+a[j].first*a[j].second;
        }
       }
       return ans;
    }
};
