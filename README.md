
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


## Acknowledgements

 - [Binary Search](https://github.com/divyalalwani64/leetcode/binarysearch)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)
 - [Majority Element](https://github.com/divyalalwani64/leetcode#majority)





#majority



## Roadmap

- Additional browser support

- Add more integrations

Getting started with Markdown
=============================


- [Getting started with Markdown](#getting-started-with-markdown)
- [Titles](#titles)
- [Paragraph](#paragraph)
- [Majority Element](#majority_element)
	- [List CheckBox](#list-checkbox)
- [Majority Element2](#majority_element2)
	- [Anchor links](#anchor-links)
- [Container With Most Water](#container_with_most_water)
- [Sort List](#sort_list)
- [Is Subsequence](#is_subsequence)
- [Excel Sheet Column Number](#excel_sheet_column_number)
- [Maximum Consecutive Ones](#max_consecutive_ones)
- [Email](#email)
- [Table](#table)
	- [Table Align](#table-align)
    	- [Align Center](#align-center)
    	- [Align Left](#align-left)
    	- [Align Right](#align-right)
- [Escape Characters](#escape-characters)
- [Emoji](#emoji)
- [Shields Badges](#Shields-Badges)
- [Markdown Editor](#markdown-editor)
- [Some links for more in depth learning](#some-links-for-more-in-depth-learning)

----------------------------------

# Titles 

### Title 1
### Title 2

	Title 1
	========================
	Title 2 
	------------------------

# Title 1
## Title 2
### Title 3
#### Title 4
##### Title 5
###### Title 6

    # Title 1
    ## Title 2
    ### Title 3    
    #### Title 4
    ##### Title 5
    ###### Title 6    

# Paragraph
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed dictum, nibh eu commodo posuere, ligula ante dictum neque, vitae pharetra mauris mi a velit. Phasellus eleifend egestas diam, id tincidunt arcu dictum quis. Pellentesque eu dui tempus, tempus massa sed, eleifend tortor. Donec in sem in erat iaculis tincidunt. Fusce condimentum hendrerit turpis nec vehicula. Aliquam finibus nisi vel eros lobortis dictum. Etiam congue tortor libero, quis faucibus ligula gravida a. Suspendisse non pulvinar nisl. Sed malesuada, felis vitae consequat gravida, dui ligula suscipit ligula, nec elementum nulla sem vel dolor. Vivamus augue elit, venenatis non lorem in, volutpat placerat turpis. Nullam et libero at eros vulputate auctor. Duis sed pharetra lacus. Sed egestas ligula vitae libero aliquet, ac imperdiet est ullamcorper. Sed dapibus sem tempus eros dignissim, ac suscipit lectus dapibus. Proin sagittis diam vel urna volutpat, vel ullamcorper urna lobortis. Suspendisse potenti.

Nulla varius risus sapien, nec fringilla massa facilisis sed. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nunc vel ornare erat, eget rhoncus lectus. Suspendisse interdum scelerisque molestie. Aliquam convallis consectetur lorem ut consectetur. Nullam massa libero, cursus et porta ac, consequat eget nibh. Sed faucibus nisl augue, non viverra justo sagittis venenatis.

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed dictum, nibh eu commodo posuere, ligula ante dictum neque, vitae pharetra mauris mi a velit. 
    
    Phasellus eleifend egestas diam, id tincidunt arcu dictum quis.
    
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

Algorithm:
1.we will iterate through all the elements.
2. if element is 1, will increase the counter.
3. else, will compare that counter has the max value, and reintialize counter to 0.
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

