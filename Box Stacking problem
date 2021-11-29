// { Driver Code Starts
#include<bits/stdc++.h>

using namespace std;

int maxHeight(int height[],int width[],int length[],int n);

int main()
{
int t;
cin>>t;
while(t--){
int n;
cin>>n;


  int A[1000],B[1000],C[10001];
for(int i=0;i<n;i++)
{
int a,b,c;
cin>>a>>b>>c;
A[i]=a;
B[i]=b;
C[i]=c;
}
cout<<maxHeight(A,B,C,n)<<endl;
}
 
} // } Driver Code Ends


/*The function takes an array of heights, width and
length as its 3 arguments where each index i value
determines the height, width, length of the ith box.
Here n is the total no of boxes.*/
struct box {
    int h,w,l;
};

bool compare(struct box a,struct box b)
{
    return (a.w*a.l > b.w*b.l)?true:false;
}

int maxHeight(int height[],int width[],int length[],int n)
{
    //STEP-1:Make an array of box (to store-> h,w,l)
    int len = 3*n;
    box arr[len];   //store  all 3 orientations
    int index = 0;
    for(int i=0;i<n;++i)
    {
        arr[index].h = height[i];
        arr[index].w = max(width[i],length[i]);
        arr[index].l = min(width[i],length[i]);
        index+=1;
       
        arr[index].h = width[i];
        arr[index].w = max(length[i],height[i]);
        arr[index].l = min(length[i],height[i]);
        index+=1;
       
        arr[index].h = length[i];
        arr[index].w = max(height[i],width[i]);
        arr[index].l = min(height[i],width[i]);
        index+=1;
    }
   
    //STEP-2: Sort in DSC order of height
    sort(arr,arr+len,compare);
   
    //STEP-3: Find LIS
    int lis[len];
    for(int i=0;i<len;++i)
        lis[i] = arr[i].h;
   
    for(int i=1;i<len;++i)
    {
        for(int j=0;j<i;++j)
        {
            if((arr[i].w < arr[j].w) and (arr[i].l < arr[j].l) and (lis[i] < lis[j]+arr[i].h))
                lis[i] = lis[j] + arr[i].h;
        }
    }
    int mx = 0;
    for(int i=0;i<len;++i)
        mx = max(mx,lis[i]);
   
    return mx;
}
