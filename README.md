# max_overlapping_prob
****Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.*****



vector<vector<int>> merge(vector<vector<int>>& ivals){
    vector<pair<int,int>>v;
    for(int i=0;i<ivals.size();i++){
        v.push_back(make_pair(ivals[i][0],ivals[i][1]));
    }
    sort(v.begin(),v.end());
    int res=0;
    for(int i=1;i<v.size();i++){
        if(v[res].second>=v[i].first){
            v[res].second=max(v[res].second,v[i].second);
            v[res].first=min(v[res].first,v[i].first);
        }
        else{
            res++;
            v[res]=v[i];
        }
    }
    vector<vector<int>>vec(res+1,vector<int>(2,0));
    for(int i=0;i<=res;i++){
        vec[i][0]=v[i].first;
        vec[i][1]=v[i].second;
    }
    return vec;
}
