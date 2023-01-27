# ncr-with-mod

int modInverse(int b, int M){
    // M should be Prime
    return Power(b%M,M-2,M);
}
int fac(int n, int M=LLONG_MAX){
    // M need not be prime here.
    if(fact[n]!=0) return fact[n];
    fact[0]=1;
    for(int i=_last_cal_; i<=n; i++){
        fact[i]=(i*fact[i-1])%M;
    }
    _last_cal_=n;
    return fact[n];
}


int nCr(int n, int r, int M){
    // M should be prime.
    if (n < r)
        return 0;
    if (r == 0)
        return 1;
    // cout<<fac(n,M)<<endl<<modInverse(r,M)<<endl<<modInverse(n-r,M)<<endl;
    return (  (  (fac(n,M)*modInverse(fac(r,M),M))%M  )  *  modInverse(fac(n-r,M),M)  )%M;
}

int nPr(int n, int r, int M){
    // M should be prime.
    if (n < r)
        return 0;
    // cout<<fac(n,M)<<endl<<modInverse(n-r,M)<<endl;
    return ( (fac(n,M)*modInverse(fac(n-r,M),M))%M  )%M;
}
