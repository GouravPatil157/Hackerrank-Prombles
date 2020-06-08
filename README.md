 //  problem 1

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        int count=0;
        count+=n/100;
        count+=(n%100)/20;
        count+=((n%100)%20)/10;
        count+=(((n%100)%20)%10)/5;
        count+=((((n%100)%20)%10)%5)/1;
        cout<<count<<endl;
    }
    return 0;
}
	
//problem 2

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
    int n;
    cin>>n;
    int a[2*n-1][2*n-1];
    int low=0,high=2*n-1,num=n;;
    while(num!=0){
        for(int i=low;i<high;i++)
            a[low][i]=num;
        for(int i=low;i<high;i++)
            a[i][high-1]=num;
        for(int i=low;i<high;i++)
            a[high-1][i]=num;
        for(int i=low;i<high;i++)
            a[i][low]=num;
        low=low+1;
        high=high-1;
        num=num-1;
    }
    for(int i=0;i<2*n-1;i++){
        for(int j=0;j<2*n-1;j++)
            cout<<a[i][j]<<" ";
        cout<<endl;
    }
    return 0;
}
	
//Problem 3

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
	int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++) cin>>a[i];
    int num1=1,num2=2,wait=3,flag=0;
    for(int i=0;i<n;i++){
        if(a[i]!=num1&&a[i]!=num2){
            flag=1;break;
        }
        num1=a[i];
        num2=wait;
        if(a[i]==3 ){
            wait=3-wait;continue;}
        if(wait==3){
            wait=3-a[i];continue;}
        else
            wait=3;
    }
    if(flag==0)
        cout<<"YES"<<endl;
    else
        cout<<"NO"<<endl;
    return 0;
}
						 
//Problem 4

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
    int n,k;
    cin>>n>>k;
    int a[n],cost=0,v[n]={0},n1,n2;
    for(int i=0;i<n;i++) cin>>a[i];
    for(int i=0;i<k;i++){
        cin>>n1>>n2;
        if(v[n1-1]==0  && v[n2-1]==0 ){
			if(a[n1-1]>a[n2-1]){
				cost+=a[n2-1];
			}
			else{
				cost+=a[n1-1];
			}
			v[n1-1]=1;
			v[n2-1]=1;
        }
        else{
            if(v[n2-1]==0 && v[n1-1]==1)
                v[n2-1]=1;
            else
                v[n1-1]=1;
        }
    }
    for(int i=0;i<n;i++){
        if(v[i]==0){
            cost+=a[i];
        }
    }
    cout<<cost;
    return 0;
}
