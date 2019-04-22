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


Review



Tip

复习了数据库设计中的各个概念，加深了对第一第二第三范式、BCNF的理解。
学习了实体关系图ER图，从抽象到具体又分为概念数据模型、逻辑数据模型、物理数据模型，接下来把工作中正在进行的对账系统概要设计的数据表画出物理数据模型。

Share

学习过程中看到了王垠的《关系模型的实质》，对于关系型数据库由不一样的见解
