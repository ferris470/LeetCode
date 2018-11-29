# LeetCode




# 栈和队列

## 相互转换


## 232. Implement Queue using Stacks (Easy)

解题思路：使用两个栈（in，out）来实现队列，注意要在输出栈没有元素的时候才可以把输入栈的元素压进去，否则会改变队头元素

  

    public int[] nextGreaterElements(int[] nums) {
        int[] ans = new int[nums.length];
        if(nums.length==0)
            return ans;
        Arrays.fill(ans,-1);
        Stack<Integer> stack = new Stack<Integer>();
        int n = nums.length;
        for(int i = 0;i<2*n;i++){
            if(stack.isEmpty()){
                stack.push(i);
                continue;
            }
            int num = nums[i%n];
            while(!stack.isEmpty()&&num>nums[stack.peek()]){
                int index = stack.pop();
                ans[index] = num;
            }
            if(i<n)
                stack.push(i);
        }
        return ans;
    }

