第5周

Algorithm

LeetCode 3. Longest Substring Without Repeating Characters
Given a string, find the length of the longest substring without repeating characters.
Example 1:
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 

Example 2:
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.



solution： Runtime: 56 ms, faster than 7.05% of Java online submissions for Two Sum. Memory Usage: 38.9 MB, less than 31.93% of Java online submissions for Two Sum.

第一版解法：
public static int lengthOfLongestSubstring(String s) {
        
        List<Integer> countList = new ArrayList<Integer>() ;
        int begin=0;
        
        if(s.length() > 1){
            for(int i = 1; i < s.length(); i++){
                
                for(int j = begin; j < i; j++){
                    if(s.charAt(i) == s.charAt(j)){                       
                        begin=j+1;
                    }                   
                }
                countList.add(i-1, i-begin+1);
            }
            int maxnum=0;
            int maxvalue=countList.get(0);
            for(int c=0; c < countList.size()-1;c++){
                if(countList.get(c+1) > maxvalue){
                	maxvalue=countList.get(c+1);
                   maxnum=c+1;
                }
            }
            System.out.println(maxnum);
            System.out.println(countList);
            return countList.get(maxnum);
        }
        else 
            return s.length();
    }
修改后：
class Solution {
    public int lengthOfLongestSubstring(String s) {
      int begin = 0;
		
		if (s.length() > 1) {
			int maxSubLength=0;
			int subLength=0;
			for (int i = 1; i < s.length(); i++) {

				for (int j = begin; j < i; j++) {
					if (s.charAt(i) == s.charAt(j)) {
						begin = j + 1;
					}
				}
				subLength = i - begin + 1;
				if(maxSubLength < subLength) maxSubLength = subLength;
			}			
			return maxSubLength;
			
		} else
			return s.length();
  
    }
}
本想缩减内存，修改后内存没变化，速度提了10%。
算法时间复杂度O(n²)

Review
最近在学习设计模式，找到一本英文书，里面介绍了Java 的 visitor pattern观察者模式是如何从无到有，一步一步“发明”出来的。
篇幅较长，刚刚开头，抽时间跟随作者把书立的例子敲一遍加深理解。
《A Little Java, A Few Patterns》
Matthias Felleisen
Daniel P. Friedman


Tip

复习了数据库设计中的各个概念，加深了对第一第二第三范式、BCNF的理解。
学习了实体关系图ER图，从抽象到具体又分为概念数据模型、逻辑数据模型、物理数据模型，接下来把工作中正在进行的对账系统概要设计的数据表画出物理数据模型。

Share

学习过程中看到了王垠的《关系模型的实质》，对于关系型数据库有一些独到的见解。
http://www.yinwang.org/blog-cn/2014/04/24/relational
1.“很多人把关系式理论和数据库独立开来，认为它们是完全不同的领域。而其实，数据结构的理论，可以很容易的解释所有关系式数据库里面的操作。
关系模型的每一个“关系”或者“行”（row），表示的不过是一个普通语言里的“结构”，就像C语言的struct。一个表（table），其实不过是某种结构的数组。”
学数据库时，不要把概念都隔离开，理解到一定程度，便发现王垠说的很对，本质上说都是存储数据的结构。只是存储的位置和查询频次、方式等角度的区别。
2.“所以关系模型所能表达的东西，其实不会超过普通程序语言所用的数据结构，然而关系模型，却具有比数据结构更多的局限。由于“行”只能有固定的宽度，所以导致了你没法在里面放进任何“变长”的对象。”
比如数据无法放进行里，最近我工作中的对账系统数据表设计就是如此，要存类似数组的数据时拆出了第二张表。这么一想，确实如王垠所说，关系型数据库的设计不够灵活，使用起来很容易出现这种必须牺牲性能的问题。
文章后面讲到了非关系型数据库，nosql和列模式数据库对以上问题的一些改进，由于没有学习和使用过非关系型数据库，这里只做记录，不予总结评价。

