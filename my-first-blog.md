# 2025.12.6星期六
欢迎来到Leon的 GitHub 博客！

## 名字
由于Leon这个名字在外国颇为常见，所以为了避免重名，我起名叫做leonnnn11.

我会在这里  
- 分享学习到的算法
- 个人制作游戏的代码（制作周期长）
- 学习的前端代码（因为未来不打算发展前端，所以只做基本的学习）
- 以及生活方面部分想要分享的东西

这是昨天晚上codeforces的div2的A题，B题就已经涉及到动态dp了，华工ACM队也在教动态dp，由于我没有数据结构基础，所以现在还不能直接学习dp。

附上A题的题目，这段时间已经开始尝试写可读性更强的代码，abc这中变量名在减少使用

算法：模拟and贪心

```cpp
/*
A. Sleeping Through Classes
time limit per test1 second
memory limit per test256 megabytes
You have n
 classes today, which are numbered from 1
 to n
.

The classes are described by a binary string∗
 s
 of length n
. We call class i
 important if and only if si=1
. For each important class, you must stay awake and listen to it.

You are very tired and wish to sleep through as many classes as possible. However, falling asleep takes time. If you listen to an important class i
, then you cannot fall asleep for the next k
 classes, i.e., you must also stay awake in classes i+1,i+2,…,i+k
 (or until the end of the day, if fewer than k
 classes remain).

For classes that are not important, you may sleep through them unless the rule above forces you to stay awake.

Your task is to find out the maximum number of classes you can sleep through today.

∗
A binary string is a string where each character is either 0
 or 1
.

Input
Each test contains multiple test cases. The first line contains the number of test cases t
 (1≤t≤500
). The description of the test cases follows.

The first line of each test case contains two integers n
 and k
 (1≤n,k≤100
).

The second line of each test case contains the string s
 of length n
 (si=0
 or 1
).

Output
For each test case, output a single integer — the maximum number of classes you can sleep through today.

Example
InputCopy
4
4 1
1001
3 3
000
3 1
001
8 2
01000101
OutputCopy
1
3
2
2
Note
In the first test case, you must listen to class 1
 and class 4
. After listening to class 1
, you cannot fall asleep in class 2
. So the only class you can sleep through is class 3
.

In the second test case, you can sleep through all the classes.

In the fourth test case, you can only sleep through classes 1 and 5.

*/
```

```cpp
#include<iostream>
using namespace std;
int main()
{
	int n;
	cin>>n;
	for(int i=0;i<n;i++)
	{
		int len,still,sum=0;
		cin>>len>>still;
		string A;
		cin>>A;
		for(int j=0;j<len;j++)
		{
			if(A[j]=='1')
			{
				for(int k=1;k<=still;k++)
				{
					if(j+k<len&&A[j+k]=='0')
					{
						A[j+k]='2';
					}
				}
			}
		}
		for(int f=0;f<len;f++)
		{
			if(A[f]=='0')
			{
				sum++;
			}
		}
		cout<<sum<<endl;		
	}
	return 0;
}
```
