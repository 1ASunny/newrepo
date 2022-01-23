STL·sort

algorithm库

template <class RandomAccessIterator>
 void sort ( RandomAccessIterator first, RandomAccessIterator last );
template <class RandomAccessIterator, class Compare>
 void sort ( RandomAccessIterator first, RandomAccessIterator last, Compare comp );

第一种：void sort ( RandomAccessIterator first, RandomAccessIterator last );

默认升序

第二种：

bool cmp判断函数

struct pair1{
int a;int b;
};
bool cmp(pair1 a,pair1 b){
return a.a<b.a;
}
int main(){
int t;cin>>t;
while(t--){
pair1 a[N];int n,k;cin>>n>>k;
for(i,1,n) cin>>a[i].a;_for(i,1,n) cin>>a[i].b;sort(a+1,a+1+n,cmp);

