# leetcode
answers to leetcode
public class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int[]res=new int[nums.length-k+1];
         if(nums==null || k==0 || nums.length-k<0)
            return new int[0];
        Queue<Integer>window=new PriorityQueue<Integer>(new Comparator<Integer>(){
            @Override
            public int compare(Integer i1, Integer i2){
                return Integer.compare(i2,i1);
            }
        }
            );
        
        for(int i=0;i<k;i++)
        window.add(nums[i]);
        res[0]=window.peek();
        for(int i=k;i<nums.length;i++)
        {
            window.remove(nums[i-k]);
            window.add(nums[i]);
            res[i-k+1]=window.peek();
        }
        return res;
        
    }
}
