
# HW4 EE538 - Computing Principles for Electrical Engineers

- Please clone the repository, edit [README.md](README.md) to answer the questions, and fill up functions to finish the HW.
- For non-coding questions, you will find **Answer** below each question. Please write your answer there.
- For coding questions, please make sure that your code can run ```bazel run/test```. In this homework, you will need to fill up [cpplib.cc](src/lib/cpplib.cc) and tests in [tests](tests).
- For submission, please push your answers to Github before the deadline.
- Deadline: Wednesday, October 20th by 23:59 pm
- Total: 120 points. 100 points is considered full credit.

## Question 1 (80 Points. Medium)

Please implement the following class for MaxHeap:
- Provide Gtest for methods that are marked with "GT".
```c++
class MaxHeap {
 public:
  MaxHeap(); // default constructor

  int getParentIndex(int i); //GT
  int getLeftIndex(int i); //GT
  int getRightIndex(int i); //GT
  int getLargestChildIndex(int i); //GT

  int getLeft(int i);
  int getRight(int i);
  int getParent(int i);

  int top(); //GT
  void push(int v); //GT
  void pop(); //GT
  void TrickleUp(int i);
  void TrickleDown(int i);

  vector<int> data_;
};
```

Write several tests using GTest for your function in [tests/q1_student_test.cc](tests/q1_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q1_student_test
```

## Question 2 (20 Points. Medium)

Write a function ```int findKthSmallest(const vector<vector<int>> &input, int k)``` that finds the kth smallest element among all elements in all vectors and returns that value.
- You should do this without sorting the vector
- Provide time complexity for your function
- if k is invalid(eg: k <= 0), return -INX_MAX

Example:\
input: [ [0, 2], [1, 5], [6, 3, 15] ] and k = 2\
output: 1

input: [ [0, 2], [1, 2, 5], [6, 2, 2, 3, 15] ] and k = 7\
output: 3

Write several tests using GTest for your function in [tests/q2_student_test.cc](tests/q2_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q2_student_test
```

## Question 3 (20 Points. Hard)

Write a function ```vector<vector<int>> kClosest(vector<vector<int>>& points, int k)```

Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane and an integer k, return the k closest points to the origin (0, 0). The distance between two points on the X-Y plane is the Euclidean distance (i.e., √(x1 - x2)^2 + (y1 - y2)^2). You should return the answer from the closest to the farthest. The answer is guaranteed to be unique (except for the order that it is in).

Example 1:\
Input: points = [[1,3],[-2,2]], k = 1\
Output: [[-2,2]]\
Explanation:\
The distance between (1, 3) and the origin is sqrt(10).\
The distance between (-2, 2) and the origin is sqrt(8).\
Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.\
We only want the closest k = 1 points from the origin, so the answer is just [[-2,2]].\
Example 2:\
Input: points = [[3,3],[5,-1],[-2,4]], k = 2\
Output: [[3,3],[-2,4]]

Write several tests using GTest for your function in [tests/q3_student_test.cc](tests/q3_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.

```
bazel test tests:q3_student_test
```

## Optional Question (No Credit - Hard)

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order. 
Write a function ```ListNode* mergeKLists(vector<ListNode*>& lists)``` that merge all the linked-lists into one sorted linked-list and return it.

Example:\
Input: lists = [[1,4,5],[1,3,4],[2,6]]\
Output: [1,1,2,3,4,4,5,6]\
Explanation: The linked-lists are:\
[\
  1->4->5,\
  1->3->4,\
  2->6\
]\
merging them into one sorted list:
1->1->2->3->4->4->5->6