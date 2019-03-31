第2周

Algorithm

LeetCode 	
1.Two Sum   
给出一个数组，返回两个相加等于特定结果的元素下标。
solution：
Runtime: 56 ms, faster than 7.05% of Java online submissions for Two Sum.
Memory Usage: 38.9 MB, less than 31.93% of Java online submissions for Two Sum.

class Solution {
    public int[] twoSum(int[] nums, int target) {
        int len = nums.length;        
        int[] result = new int[2];
        for(int i = 0; i < len-1; i++){
            for(int j = i+1; j < len; j++)
                if (nums[i] + nums[j] == target){
                    result[0] = i;
                    result[1] = j;
                }                    
        }
        return result;            
    }
}
自己写的算法太基础，更优解法思路贴在下面，下周根据思路来实现。
The general idea is:
step1 : copy an array, and sort it using quick sort, O(nlogn)
step2 : using start and end points to find a, b which satifys a+b==target, O(n)
step3 : find the index of a, b from origin array, O(n)
note: in step3, you should judge whethour a==b, if true, you must find the second index of b.

Review 

1.
对于刚刚发布的JDK 12，了解了这一版本的一些新特性。
因为有为项目组成员播报技术动向的任务，便针对JDK 12的新特性switch的表达式写法，给项目组小伙伴出了道趣味题
过程中阅读了http://openjdk.java.net/jeps/325
2.
目前的工作任务中用到了针对pbs调度器的记账系统-Gold，年代比较久远的一款产品。阅读了Gold相关的英文技术资料，研究了其数据库构成，各命令可查询的信息。
发现Gold设计过程中缺少账号余额变化的记录，每次扣费、充值、回退等行为发生前后的账号余额没有记录，这对账号金额连续性检查造成障碍。

Tip

环境变量问题，linux的crontab定时任务未生效
    分析过程：
1） 在定时执行的check_acct_parsing_process.sh中 增加打印日志语句
   -> 没打印日志
2）手动执行check_acct_parsing_process.sh,
   - > 打印了日志
3）查看crontab日志/etc/init.d/cron
   -> 有定时执行记录
4）在check_acct_parsing_process.sh中不同位置增加打印日志
    -> 只打印了脚本开头第一处的日志
    -> if [ -z $GRIDVIEW_HOME ] 判断为真，执行力if里的exit 1 
  解决方法： 脚本开头增加source /etc/profile.d/dawning.sh
  原因：不要假定cron知道所需要的特殊环境，它其实并不知道。所以你要保证在shelll脚本中提供所有必要的路径和环境变量
  
Share

这周阅读学习了《重构》的8.1-9.7。
第八章的重构手法，有些不常用，有些很基础，代码第一遍写时就会遵循，还有些不容易分辨何时引入此重构方法。
目前印象比较深刻的是9.7引入Null对象的重构手法，接下来一周里会做练习使用这一重构方法，加深理解后总结这一方法的优缺点。

https://mp.weixin.qq.com/s/y2I_EYSLlq_239vZXr0OZQ?
