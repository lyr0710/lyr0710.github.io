4. Median of Two Sorted Arrays
There are two sorted arrays nums1 and nums2 of size m and n respectively.
Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).
You may assume nums1 and nums2 cannot be both empty.

Example 1:
nums1 = [1, 3]
nums2 = [2]
The median is 2.0

Example 2:
nums1 = [1, 2]
nums2 = [3, 4]
The median is (2 + 3)/2 = 2.5


class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        double median = 0;
        int m = nums1.length;
        int n = nums2.length;
        String position;
        if( (m+n) % 2==0 )
            position = "even";
        else 
            position = "odd";
        if(n !=0 && m !=0){
	        if (nums2[0] > nums1[m-1]){            //第二个数组的第一个元素 大于 第一个数组的最后一个元素
	            if(m > n){                   //寻找下标中位
	                if("even".equals(position))    //两个数组一共偶数个元素
	                    median = (double)(nums1[(m+n)/2] + nums1[(m+n)/2 - 1])/2;
	                else                           //两个数组一共奇数个元素
	                    median =  nums1[(m+n-1)/2];
	            }else if(m < n){
	            	            	
	            	if("even".equals(position)){    //两个数组一共偶数个元素
	            		
	                    median = (double)(nums2[(n-m)/2] + nums2[(n-m)/2 - 1])/2;
	            	}
	                else                           //两个数组一共奇数个元素
	                    median =  nums2[(n-m-1)/2];
	            }else{
	            	median = (double)(nums1[m-1] + nums2[0]) / 2;
	            }
	        }else if (nums2[n-1] < nums1[0]){            //第二个数组的最后一个元素 小于 第一个数组的第一个元素
	        	System.out.println(111);
	        	
	            if(n > m){                   //寻找下标中位
	                if("even".equals(position))    //两个数组一共偶数个元素
	                    median = (double)(nums2[(m+n)/2] + nums2[(m+n)/2 - 1])/2;
	                else                           //两个数组一共奇数个元素
	                    median =  nums2[(m+n-1)/2];
	            }else if(n < m){
	            	            	
	            	if("even".equals(position)){    //两个数组一共偶数个元素
	            		
	                    median = (double)(nums1[(m-n)/2] + nums1[(m-n)/2 - 1])/2;
	            	}
	                else                           //两个数组一共奇数个元素
	                    median =  nums1[(m-n-1)/2];
	            }else
	            	median = (double)(nums1[0] + nums2[n-1]) / 2;
	        }else{
	        	int[] combine;
	        	int end = 0;
	        	if("even".equals(position)){
	        		end = (m + n) / 2;
	        		combine = new int[(m + n) / 2 + 1];
	        	}	
	        	else{
	        		end = (m + n - 1) / 2;
	        		combine = new int[(m + n + 1) / 2 ];
	        	}
	        	int p1 = 0;
	    		int p2 = 0; 
	        	for(int i=0; i <= end; i++){     	       			       		
	        		if(p1 == m) {
	        			combine[i] = nums2[p2];
	        			p2++;
	        		}else if (p2 == n) {
	        			combine[i] = nums1[p1];
	        			p1++;
	        		}else {
	        			if(nums1[p1] < nums2[p2]){
	 
		        			combine[i] = nums1[p1];
		        			p1++;        	

		        		}else{

		        			combine[i] = nums2[p2];
		        			p2++;
		        		}
	        		}        		
	        	}
	        	
	        	if("even".equals(position)){

	        		median = (double)(combine[combine.length - 1] + combine[combine.length - 2]) / 2;
	        	}else{
	        		median = combine[combine.length - 1];
	        	}        
	        }
        }else if( m==0 ){
        	if("even".equals(position))    //两个数组一共偶数个元素
                median = (double)(nums2[n/2] + nums2[n/2 - 1])/2;
            else                           //两个数组一共奇数个元素
                median =  nums2[(n-1)/2];      
        }else if( n==0 ){
        	if("even".equals(position))    //两个数组一共偶数个元素
                median = (double)(nums1[m/2] + nums1[m/2 - 1])/2;
            else                           //两个数组一共奇数个元素
                median =  nums1[(m-1)/2];      
        }
        return median;  
    }
}


Runtime: 3 ms, faster than 73.59% of Java online submissions for Median of Two Sorted Arrays.
Memory Usage: 48.5 MB, less than 81.09% of Java online submissions for Median of Two Sorted Arrays.
