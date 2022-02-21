
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
 - [Majority Element](#majority)





#majority



## Roadmap

- Additional browser support

- Add more integrations

