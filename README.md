
# Hi, I'm Divya! 👋


## LeetCode Solved Problems

[Binary Search](https://linktodocumentation)

Problem: Given a sorted array arr[] of n elements, write a function to search a given element x in arr[].

Binary Search Approach: Binary Search is a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(Log n).





## Algorithm

```bash
  int low = 0, right = arr.length - 1;
        while (low <= right) {
            int mid = low + (right - low) / 2;
            if (arr[mid] == x)  // Check if x is present at mid
                return id;
            if (arr[mid] < x)  // If x greater, ignore left half
                low = mid + 1;
            else              // If x is smaller, ignore right half
                right = mid - 1;
        }
```

Getting started with Markdown
=============================

- [Majority Element](#majority_element)
- [Majority Element2](#majority_element2)
- [Container With Most Water](#container_with_most_water)
- [Sort List](#sort_list)
- [Is Subsequence](#is_subsequence)
- [Excel Sheet Column Number](#excel_sheet_column_number)
- [Maximum Consecutive Ones](#max_consecutive_ones)
- [Subsets](#subsets)
- [Diameter of Binary Tree](#diameter_of_binary_tree)
- [Inorder traversal of tree](#inorder_traversal_of_tree)
- [Preorder traversal of tree](#preorder_traversal_of_tree)
- [Copy_List_With_Random_Pointer](#copy_list_with_random_pointer)
- [Best time to buy and sell stocks-2](#best_time_to_buy_and_sell_stocks)
- [Delete and Earn](#delete_and_earn)


----------------------------------
    
# Majority_Element
Given an array nums of size n, return the majority element.</br>
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.</br>

Example 1:</br>
Input: nums = [3,2,3]</br>
Output: 3</br>

We can solve it with the help of hashmap.</br>
1.Store the element and its count in hashmap.</br>
2.If count> n/2 , we will return that element.</br>
```bash
class Solution {
    public int majorityElement(int[] nums) {
        int len=nums.length - 1;
        HashMap<Integer, Integer> hm= new HashMap();
        for(int i=0;i< nums.length;i++)
        {
            hm.put(nums[i],hm.getOrDefault(nums[i],0)+1);
            int n = hm.get(nums[i]);
            if(n > (len/2) )
                return nums[i];
        }
        return 0;
    }
}
```

# Majority_Element2

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.<br/>

Example 1:<br/>
Input: nums = [3,2,3]<br/>
Output: [3]<br/>

We can solve it with the help of hashmap and arrayList for storing the output.</br>
1.Store the element and its count in hashmap.</br>
2.If count> n/3 && element is not there in arrayList , we will store that element in arrayList.</br>
```bash
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        int len=nums.length;
        List<Integer> majority= new ArrayList<>();
        HashMap<Integer, Integer> hm=new HashMap<>();
        for(int i=0;i<nums.length;i++)
        {
            hm.put(nums[i], hm.getOrDefault(nums[i],0)+1);
            int n=hm.get(nums[i]);
            if(n> len/3 && !majority.contains(nums[i]))
                majority.add(nums[i]);
        }
        return majority;
    }
}
```

# Container_With_Most_Water
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).</br>

Find two lines that together with the x-axis form a container, such that the container contains the most water.</br>

Return the maximum amount of water a container can store.</br>

Notice that you may not slant the container.</br>

![image](https://user-images.githubusercontent.com/97536928/155071305-cf13c4e7-b0a7-4ae4-87ea-7ff7b6ace638.png)

1. We can solve it using Two Pointers.</br>
2. Take i =0 and j=len-1;</br>
3. If height[i] < height[j] , we will increase i++ , else j--.</br>
```bash
class Solution {
    public int maxArea(int[] height) {
        int i=0, j=height.length-1, max=Integer.MIN_VALUE,product;
        while(i<j)
        {
            product=1;
            if(height[i]>height[j])
            {
                product=height[j]*(j-i);
                j--;
            }
            else
            {
                product=height[i]*(j-i);
                i++;
            }
            max=Math.max(max,product);
        }
        return max;
    }
}
```

# Sort_List

Given the head of a linked list, return the list after sorting it in ascending order.</br>
![image](https://user-images.githubusercontent.com/97536928/155078054-8dfbb539-f56a-4347-ae70-1b9f17cab005.png)

 Merge Sort is one of the efficient sorting algorithms that is popularly used for sorting the linked list.</br>
 
 Algorithm:</br>
 1.Recursively divide the list on basis of start and mid (find mid with help of slow and fast pointer).</br>
 2.Merge the divided the list , using merge two sorted list concept.</br>

```bash
class Solution {
    public ListNode sortList(ListNode head) {
        if(head==null || head.next==null)
            return head;
        ListNode mid=getMid(head);
        ListNode left=sortList(head);
        ListNode right= sortList(mid);
        return merge(left, right);
    }
    public ListNode merge(ListNode list1, ListNode list2)
    {
        ListNode temp=new ListNode(0);
        ListNode dummyhead= temp;
        while(list1!=null && list2!=null)
        {
            if(list1.val< list2.val)
            {
                temp.next = list1;
                list1=list1.next;
            }
            else
            {
                 temp.next = list2;
                 list2=list2.next;
            }
            temp=temp.next;
        }
        if(list1!=null)
            temp.next=list1;
        if(list2!=null)
            temp.next=list2;
        return dummyhead.next;
    }
    public ListNode getMid(ListNode head)
    {
        ListNode mid=head, fast=head, prev=null;
        while(fast!=null && fast.next!=null)
        {
            prev=mid; // we will also keep track of previous of mid, so that we can break the link from start to midprev and mid to end
            mid=mid.next;
            fast=fast.next.next;
        }   
        prev.next=null;// here we are assigning prev of next to null, break the link.
        return mid;
    }
}
```

# Is_Subsequence

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.</br>

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).</br>

 Example 1:</br>

Input: s = "abc", t = "ahbgdc"</br>
Output: true</br>

Algorithm:</br>
1.Take two pointers i for s and j for t initialize with 0 .</br>
2.Increment i if s.charAt(i) == t.charAt(j) and increment j at every step.</br>
3.if i equals length of s , return true , else return false.</br>

```bash
class Solution {
    public boolean isSubsequence(String s, String t) {
        int len1=t.length() , len2=s.length();
        int i=0,j=0;
        while(j<len1 && i<len2)
        {
            if(s.charAt(i) == t.charAt(j))
                i++;
            j++;
        }
        if(i==len2)
            return true;
        else
            return false;
    }
}
```
 
 # Excel_Sheet_Column_Number
 
 Given a string columnTitle that represents the column title as appear in an Excel sheet, return its corresponding column number.<br/>

For example:<br/>
A -> 1<br/>
B -> 2<br/>
C -> 3<br/>
...<br/>
Z -> 26<br/>
AA -> 27<br/>
AB -> 28 <br/>
...<br/>

For every additional digit of the string, we multiply the value of the digit by 26^n where n is the number of digits it is away from the one's place. This is similar to how the number 254 could be broken down as this: (2 x 10 x 10) + (5 x 10) + (4). The reason we use 26 instead of 10 is because 26 is our base.<br/>

For s = "BCM" the final solution would be (2 x 26 x 26) + (3 x 26) + (13)<br/>

We could do this process iteratively. Start at looking at the first digit "B". Add the int equivalent of "B" to the running sum and continue. Every time we look at the following digit multiply our running sum by 26 before adding the next digit to signify we are changing places. Example below:<br/>

"B" = 2<br/>
"BC" = (2)26 + 3<br/>
"BCM" = (2(26) + 3)26 + 13<br/>

```bash
class Solution {
    public int titleToNumber(String columnTitle) {
       if(columnTitle.length()==0)
           return -1;
        int sum=0;
        for(char ch: columnTitle.toUpperCase().toCharArray())
            sum=sum*26 + ch-'A'+1;
        return sum;
    }
}
```

# Max_Consecutive_Ones
Given a binary array nums, return the maximum number of consecutive 1's in the array.</br>

Example 1:</br>
Input: nums = [1,1,0,1,1,1]</br>
Output: 3</br>
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.</br>

Algorithm:</br>
1.we will iterate through all the elements.</br>
2. if element is 1, will increase the counter.</br>
3. else, will compare that counter has the max value, and reintialize counter to 0.</br>
```bash
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int sum=0, max=0;
        for(int i=0;i<nums.length;i++)
        {
            if(nums[i]==1 )
            {
                sum=sum+1;
            }
            else if(nums[i]==0)
            {
                if(sum>=max)
                    max= sum;
                sum=0;
            }
        }
        if(sum>=max)// it is because possibly last number couldn't be zero.
            max=sum;
        return max;
        
    }
}
```

# Subsets
Subsets are the power sets, for n elements, no. of subsets will be 2^n </br>
1.Iterative Approach</br>
eg: [1,2,3]</br>
result set- []</br>
copy all sets from result set, and add 2nd element in it [1] and paste back in Result = [],[1]</br>
copy all sets from result set, and add 2nd element in it [2],[1,2] and paste back in Result =[],[1],[2],[1,2]</br>
copy all sets from result set, and add 2nd element in it [3], [1,3],[2,3], [1,2,3] and paste back in Result =[],[1],[2],[1,2],[3], [1,3],[2,3], [1,2,3]</br>

```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res=new ArrayList();
        res.add(new ArrayList());//adding empty list
        for(int i=0;i<nums.length;i++)
        {
            int s=res.size();
            for(int j=0;j<s;j++)
            {
                List<Integer> temp=new ArrayList(res.get(j));//retrieving elems from res
                temp.add(nums[i]);//adding nums[i] to retrieved elems
                res.add(temp);//adding updated element back to res.
            }          
        }
        return res;
    }
}
```

2. Recursion
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res= new ArrayList();
        generateSubsets(0,nums,res, new ArrayList());//passing only start as it will move for all elements till end depending on start.
        return res;
    }
    public void generateSubsets(int start,int[] nums, List<List<Integer>> res, List<Integer> curr)
    {
        res.add(new ArrayList(curr));
        for(int i=start;i<nums.length;i++)
        {
            curr.add(nums[i]);
            generateSubsets(i+1,nums,res,curr);// this will execute first till like dfs
            curr.remove(curr.size()-1);//backtrack and remove the last element
        }
    }
}
```

# Diameter_Of_Binary_Tree

Given the root of a binary tree, return the length of the diameter of the tree.</br>
The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.</br>
The length of a path between two nodes is represented by the number of edges between them.</br>
![image](https://user-images.githubusercontent.com/97536928/156914115-a4b9965f-1845-4eb2-9644-ba00701b15cd.png)

Algorithm:
1.Diameter can be the height of left subtree + right subtree.</br>
2. It can be in left subtree, i.e left diameter</br>
3. Or it can be in right subtree i.e right diameter</br>
4. Therefore it will be max(left+right, leftdia, rightdia)</br>

```
class Solution {
    public int diameterOfBinaryTree(TreeNode root) {
        if(root==null)
            return 0;
        int lheight= height(root.left);
        int rheight= height(root.right);
        int ldia=diameterOfBinaryTree(root.left);
        int rdia=diameterOfBinaryTree(root.right);
        return Math.max(lheight+rheight,Math.max(ldia,rdia));
        
        
    }
    public int height(TreeNode root)
    {
        if(root==null)
            return 0;
        return Math.max(height(root.left), height(root.right))+1;
    }
}
```


# Inorder_Traversal_Of_Tree

Algorithm:</br>
1.Create a stack.</br>
2.Initialize currentNode = root</br>
3.while true</br>
  while(currentNode !=null)</br>
    push currentNode in stack.</br>
    currentNode= currentNode.stack.</br>
  if stack is empty</br>
    break</br>
  currentNode= stack.pop()</br>
  Add currentNode.value in result</br>
  currentNode=currentNode.right</br>

```
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        //Iterative approach
        List<Integer> result=new ArrayList();
        Stack<TreeNode> inorder= new Stack<>();
        TreeNode current=root;
        while(true)//because we have terminating condition inside the loop.
        {
            while(current!=null)
            {
                inorder.push(current);
                current=current.left;
            }
            if(inorder.isEmpty())//terminating condition
                break;
            current=inorder.pop();
            result.add(current.val);
            current=current.right;
        }
        
        return result;
    }
}
```
  
 
# Preorder_Traversal_Of_Tree 
Algorithm:</br>
1.Create a stack.</br>
2.Initialize currentNode = root</br>
3.while true</br>
  while(currentNode !=null)</br>
    Add currentNode.value in result</br>
    push currentNode in stack.</br>
    currentNode= currentNode.stack.</br>
  if stack is empty</br>
    break</br>
  currentNode= stack.pop()</br>
  currentNode=currentNode.right</br>
  
  ```
  class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        Stack<TreeNode> preorder= new Stack();
        List<Integer> result= new ArrayList();
        TreeNode current=root;
        while(true)
        {
            while(current!=null)
            {
                result.add(current.val); // preorder 
                preorder.push(current);
                current=current.left;
            }
            if(preorder.isEmpty()) break;
            current=preorder.pop();
            current=current.right;
        }
        return result;
    }
}
```

# Copy_List_With_Random_Pointer
1.Brute Force Approach</br>
Algo: </br>
1.will take a hashmap<Node,Node> which stores node and create a new node with its value.</br>
2.Then will link the nodes.</br>

```

//Brute force approach
//1.TimeComplexity = O(n)+O(n) = O(n)
//2.SpaceComplexity = O(n) -> for hashmap
class Solution {
    public Node copyRandomList(Node head) {
        HashMap<Node,Node> map =new HashMap<>();
        Node randomNode= head;
        //storing node and creating new node in hashmap.
        while(randomNode!=null)
        {
            map.put(randomNode, new Node(randomNode.val));
            randomNode=randomNode.next;
        }
        randomNode=head;
        //Linking nodes
        while(randomNode!=null)
        {
            map.get(randomNode).next=map.get(randomNode.next);
            map.get(randomNode).random=map.get(randomNode.random);
            randomNode=randomNode.next;
        }
        return map.get(head);
        
    }
}
```

2.Optimized Approach</br>
//1.Create a deep copy of node and paste copy of each node after it.</br>
//2.link the deep copies to random.</br>
//3.Extract back normal list and deep copy list.</br>

```
//1.TimeComplexity = O(n)+O(n)+O(n) = O(n)
//2.SpaceComplexity = O(1) 
class Solution {
    public Node copyRandomList(Node head) {
        Node iter=head;
        Node front=head;
        while(iter!=null && front!=null)
        {
            front=iter.next;
            Node copy= new Node(iter.val);
            iter.next=copy;
            copy.next=front;
            iter=front;
        }
        iter=head;
        while(iter!=null)
        {
            if(iter.random!=null)
               iter.next.random=iter.random.next;
           
              iter=iter.next.next;
        }
        iter=head;
        front=head;
        Node randomNode = new Node(0);
        Node randomHead=randomNode;
        while(iter!=null)
        {
            front=iter.next.next;
            randomNode.next=iter.next;
            iter.next=front;
            iter=front;
            randomNode=randomNode.next;
        }
        return randomHead.next;
        
    }
}
```

# Best_Time_To_Buy_And_Sell_Stocks-2
Algo:</br>
1.Set buying , selling date as 0, also profit as 0.</br>
2.If there is increase in price from its previous date will increase the selling date.</br>
3.If there is decrease in price, we will collect the profit and make new buy and sell date.</br>
Simple idea is to collect all the profit at each upstroke</br>
![image](https://user-images.githubusercontent.com/97536928/158050126-f148155c-ae20-4e69-8f7b-dddb30cbe02c.png)
```
class Solution {
    public int maxProfit(int[] prices) {
        int bd=0,sd=0,profit=0;//buying date is 0, selling date is 0 and also profit is 0;
        for(int i=1;i<prices.length;i++)
        {
            if(prices[i]>=prices[i-1])//if price is greater than previous price will increase the selling date
                sd++;
            else // if price is less, will calculate the profit at last collected sd and bd.
            {
                profit+=prices[sd]-prices[bd];//collect the profit
                bd=sd=i;// set new sd and bd
            }
        }
        profit+=prices[sd]-prices[bd];//collect the profit
        return profit;
        
    }
}
```

# Delete_And_Earn
You are given an integer array nums. You want to maximize the number of points you get by performing the following operation any number of times:</br>

Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete every element equal to nums[i] - 1 and every element equal to nums[i] + 1.</br>
Return the maximum number of points you can earn by applying the above operation some number of times.</br>

Example 1:</br>

Input: nums = [3,4,2]</br>
Output: 6</br>
Explanation: You can perform the following operations:</br>
- Delete 4 to earn 4 points. Consequently, 3 is also deleted. nums = [2].</br>
- Delete 2 to earn 2 points. nums = [].</br>
You earn a total of 6 points.</br>

Algorithm:
1.we can simplify nums by collecting all duplicate numbers together. As an example, nums can be represented as a hash map with numbers as keys which map to the number of times the key occurs in nums. [2, 2, 3, 3, 3, 4] would be converted to {2: 2, 3: 3, 4: 1}.</br>
Will find the max element</br>
2.Recurrence Relation:will apply it on maximum element.</br>
case 1: will consider max element, find value i.e the points we can get from max element and call function maxelement-2 as we cannot consider maxelement-1.</br>
case 2: will not consider max element , so will function with maxelement -1.</br>
3.Base Condition</br>
1.if maxNumber=0,will return 0, coz, any number multiply by 0 will be 0.</br>
2.if maxNumber=1, will return the number of time 1 is occured or else will return 0.</br>
![image](https://user-images.githubusercontent.com/97536928/158397060-94e0136b-6295-4b52-b933-2ec60bb138e4.png)



<b>Top-Down Approach</b>
We will make use of hashmap cache to store recursion data.</br>
1.first will check if has data , will return that.</br>
```
class Solution {
    HashMap<Integer,Integer> points= new HashMap();
    HashMap<Integer,Integer> cache= new HashMap();
    int maxNumber=Integer.MIN_VALUE;
    public int deleteAndEarn(int[] nums) {
        for(int n:nums)
        {
            points.put(n,points.getOrDefault(n,0)+n);
            maxNumber=Math.max(maxNumber,n);
        }
        return maxPoints(maxNumber);
    }
    public int maxPoints(int num)
    {
        if(num==0)
            return 0;
        if(num==1)
            return points.getOrDefault(1,0);
        if(cache.containsKey(num))
            return cache.get(num);
        else
        {
            int gain=points.getOrDefault(num,0);
            cache.put(num,Math.max(maxPoints(num-1),maxPoints(num-2)+gain));
        }
        return cache.get(num);
    }
}
```

<b>Bottom-Up Approach</b>
```
class Solution {
    HashMap<Integer,Integer> points= new HashMap();
    int maxNumber=Integer.MIN_VALUE;
    public int deleteAndEarn(int[] nums) {
        for(int n:nums)
        {
            points.put(n,points.getOrDefault(n,0)+n);
            maxNumber=Math.max(maxNumber,n);
        }
        
    int cache[]=new int[maxNumber+1];
        cache[0]=0;
        cache[1]= points.getOrDefault(1,0);
        for(int i=2;i<=maxNumber;i++)
        {
            int gain=points.getOrDefault(i,0);
            cache[i]=Math.max(cache[i-1],cache[i-2]+gain);
        }
        return cache[maxNumber];
}
}
```



