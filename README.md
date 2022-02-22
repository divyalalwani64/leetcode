
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
- [Image | GIF](#image--gif)
- [Style Text](#style-text)
	- [Italic](#italic)
	- [Bold](#bold)
	- [Strikethrough](#strikethrough)
- [Code](#code)
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


 
