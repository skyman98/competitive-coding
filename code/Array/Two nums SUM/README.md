

## Two nums SUM:

> In this Question, we have one int array and one target integer value. we need to find two indexes of this array whose elements sum equal to the target integer.

## Method:

> if we see it the first time, we can directly say that we can sort array and travel from left and right side if both values are less than the target then increase left pointer otherwise decrease right pointer.
 
> but if we do this we can see that we have changed all indexes of all elements, so we can create another pair<int, int> that stores index, value pair and we sort values so we have one copy of index information.

**Code:** 

    bool sortbysec(const pair<int,int> &a,
                  const pair<int,int> &b)
                {
                    return (a.second < b.second);
                }
    class Solution {
    public:
        
        vector<int> twoSum(vector<int>& arr, int target) {
            vector< pair <int,int> > ans;
            int sz=arr.size();
            for(int i=0;i<sz;i++){
                ans.push_back( make_pair(i,arr[i]) );
            }
            sort(ans.begin(), ans.end(), sortbysec);
            int left=0,right=sz-1;
            while(left < right){
                int val=ans[left].second + ans[right].second;
                if(val<target){
                    left++;
                }else if(val > target){
                    right--;
                }
                else{
                    return {ans[left].first,ans[right].first};
                }
            }
            return {};
        }
    };

**Time : O(n)
Space : O(n)**

