### Codeforces Round #839 (Div. 3) 
##### Problem - A
You are given an expression of the form a+b, where a and b are integers from 0 to 9. You have to evaluate it and print the result.

##### Approach :
We are given an expression of the form a+b. In order to evauluate this expression first we have to find the integers on which we have to perform the addition operation. because we dont know the number of digits in both integers so we can only find the value of both integers by breaking the string around the + sign. once we get the operators in string form we can convert it to integer using *stoi* function and perform the addition operation and output the result.

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
