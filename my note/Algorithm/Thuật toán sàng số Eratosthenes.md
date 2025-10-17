
Input: n
Output: số nguyên tố <= n

`vector<int> eratosthenes(int n){

    bool num[n] = {0};
    vector<int> p;
    for(int i=2;i<n;i++){
        if(!num[i]){
            p.push_back(i);
            for(int j=i*i;j<n;j+=i){
                num[j]=1;
            }
        }
    }
    return p;
}`