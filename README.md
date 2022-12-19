### Codeforces Round #839 (Div. 3) 
##### Problem - A. A+B?
You are given an expression of the form a+b, where a and b are integers from 0 to 9. You have to evaluate it and print the result.

##### Approach :
We are given an expression of the form a+b. In order to evauluate this expression first we have to find the integers on which we have to perform the addition operation. because we dont know the number of digits in both integers so we can only find the value of both integers by breaking the string around the + sign. once we get the values in string form we can convert it to integer using *stoi* function and perform the addition operation and output the result.

##### Solution (C++) :
```cpp
#include <bits/stdc++.h>
using namespace std;
 
int main() {
	int t;
	cin>>t;
	while(t--)
	{
		string s;
		cin>>s;
		int d=0;
		string op="";
		for(int i=0;i<s.size();i++)
		{
			if( s[i]=='+' || s[i]=='-'  || s[i]=='*'   || s[i]=='/' )
			{
				op=s[i];
				d = i;
				break;
			}
		}
		string a = (s.substr(0,d));
		string b = (s.substr(d+1));
		cout<< stoi(a)+stoi(b)<<endl;
	}
	return 0;
}
```

##### Problem - B. Matrix Rotation

You have a matrix 2×2 filled with distinct integers. You want your matrix to become beautiful. The matrix is beautiful if the following two conditions are satisfied:
- in each row, the first element is smaller than the second element;
- in each column, the first element is smaller than the second element.

You can perform the following operation on the matrix any number of times: rotate it clockwise by 90 degrees, so the top left element shifts to the top right cell, the top right element shifts to the bottom right cell, and so on.Determine if it is possible to make the matrix beautiful by applying zero or more operations.

##### Approach :
we are given a 2X2 matrix and we have to find whether we can make this matrix beatiful or not. a matrix is beautiful if it is row and column wise sorted. We are allowed perform 90 degree clockwise rotation on matrix as many times we want to make it beautiful. By observation we can say that for matix to be beautiful the maximum and minimum element of the matrix should be at daigonal position to each other.In 2X2 matrix if the two elements are at diagonal position to each other then sum of absolute difference between their x and y coordinates will always be greater than 1. Thus we can determine whether the matrix can be made beautiful by finding the index of the maximum and minimum element of the matrix then taking the sum of absolute difference of x and y the coordinates between them. If the sum is greater then 1 we can say that the matrix can be made beautiful.

##### Solution (C++) :
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
	int t;
	cin>>t;
	while(t--)
	{
		int ans[2][2];
		int x,y;
		int xm,ym;
		int maxi=INT_MIN;
		int mini = INT_MAX;
		for(int i=0;i<2;i++)
		{
			for(int j=0;j<2;j++)
			 {
			 	cin>>ans[i][j];
			 	if(maxi < ans[i][j])
			 	{
			 		maxi=ans[i][j];
			 		x=i;
			 		y=j;
			 	}
			 	if(mini > ans[i][j])
			 	{
			 		mini=ans[i][j];
			 		xm=i;
			 		ym=j;
			 	}
			 }
		}
		if((abs(xm-x)+abs(ym-y))>1)
		cout<<"YES"<<endl;
		else
		cout<<"NO"<<endl;
	}
	return 0;
}

```
