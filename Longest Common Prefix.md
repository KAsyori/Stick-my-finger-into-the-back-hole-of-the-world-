# Longest Common Prefix
## Description
`Write a function to find the longest common prefix string amongst an array of strings. `
## 解题思路～～什么的～～
1.既然要找最长的公共前缀，我就挨个挨个从第一个去比较每个字符数组中元素是否相同，直到不相同为止
2.所以为了避免数组越界，就要先得到最短的字符串的长度。
3.找到第一个不同的元素的角标之后，就可以返回**从第一个元素开始到这个元素的字符串**了，这个就要用到String类的substring成员方法。
## 代码
```java
class Solution {
	public  String longestCommonPrefix(String[] strs) {
        if (strs.length == 0)//如果什么都没输入自然是不会有公共前缀的
            return "";
		char prefix;int i = 0;
		int [] length1 = new int [strs.length];//创建一个数组来储存全部String类数组的长度
		for (int n = 0; n < strs.length; n++) {
			length1[n] = strs[n].length();
		}
		int minLength = Arrays.stream(length1).min().getAsInt();//然后用Arrays类的方法得到最短的长度避免下面遍历的时候越界
        if (minLength == 0)//当然如果最短的长度为0也没有公共前缀
            return "";
		while (i < minLength) {
			prefix = strs[0].charAt(i);
			for (int j = 0;j <strs.length;j ++) {//遍历字符串，比较字符
				if (prefix != strs[j].charAt(i)){
					return strs[0].substring(0,i);//有不同的就直接返回，这里注意substring方法是不包括后一个角标的字符的
				}
			} i++;
		}
			return strs[0].substring(0,i);
  }
  public static void main (String[] args) {//不得不说每次leetcode的题都在给我的主函数出难题。。。。
		System.out.println("请输入String类数组长度");
		Scanner sc = new Scanner(System.in);
		int length = sc.nextInt();
		String[] strs = new String[length];
		for (int i = 0 ;sc.hasNext(); i++) {
			strs[i] = sc.next();
		}
	//	longestCommonPrefix(strs);
		System.out.println(longestCommonPrefix(strs));
	//	System.out.println(strs[1]);
	}
}
```
## 总结
>虽然看了一下Solution，但是还是执意用自己的思路去做了，～～去他娘的Solution～～，回过头来看，其实不同的思路决定了不同的解题方法和过程。虽然最后异曲同工还是不得不承认Solution写得好一些。从最长的两个字符串开始，一步一步缩小字符串的长度，这样也不会有我的那么多特殊情况。学到了。
