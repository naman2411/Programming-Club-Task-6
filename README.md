# Joining Task
                                                                    time limit per test 1 second
                                                                    memory limit per test 256 megabytes
                                                                    input standard input
                                                                    output standard output
Alice the student of IIT Kanpur is highly interested in Coding and Development for that he want to join Programming Club of IIT Kanpur. As Programming Club is highly demanded and elite club so everyone want to join it. So Programming Club gave the task and for relaxation they allowed a pair of student to work on the task. So the task goes as: Everyone has been assigned a dataset of competitive programmers that includes the number of contest(n) given by him and an array which contains change in rating after each round and also each one of them wants to find out the index of the first rating drop in the array of rating changes for every subarray of size k . After trying the problem Alice did not get the logic of the problem so as a partner of alice you need to help him. Can you help him ??  
**Input**  
The first line of the test case consists of two integers n,k(1<k<n<1e5).-> number of elements in array and size of subarray.  
The second line consists of n integers seperated by a space.  
**Output**  
Output consists of n-k+1 elements which are indexes of first negative element in the array for
that subarray of size k. (Use 1 based indexing) if no negative element is present in subarray output -1 for that subarray.  
**Example  
input**  
7 2  
3 -2 1 0 -2 5 -1  
**output**  
2 2 -1 5 5 7   
**Explaination**  
Let's consider all subarray of size 2 in the given array, the subarrays are [0:1], [1:2], [2:3], [3:4].  
 
Now for subarray [0:1] -> [2, -4], the first negative element is present at index 2(1 based indexing), [1:2] -> [-4, 3], the first negative element is present at index 2 of the array and similarly for all the remaining subarrays.  
## Test Case Generator 
``` C++
#include <bits/stdc++.h>      
using namespace std;  
  

int randomize()   
{   
    return (rand() % 200000)-100000;  
}  
int main ()  
{  
  // for different values each time we run the code
  srand(time(NULL));   
    
   
int n = rand()%(100000)+1;  
int k = rand()%(n)+1; 
vector<int> vect(n);  
  // Fill all elements using randomize()
  generate(vect.begin(), vect.end(), randomize);  
  cout << n <<" "<< k<<endl ;  
  for (int i  = 0 ;  i< n ;  i++){  
    cout << vect[i]<<" ";  
  }  
  return 0 ;}
  ```
  ## Sample Test Cases (not included larger one )
Input  
10 3
27871 -49102 -45652 -77392 35862 -65991 -40869 73305 58235 4303
Output  
2 2 3 4 6 6 7 -1  
Input  
100 31
-61621 80968 99477 -76460 -94380 32401 11779 -3107 -37934 -39396 40131 -99641 -89189 24883 -24708 -88815 -44336 -26040 59212 -73621 -15072 55094 9771 -75517 72593 -96111 56374 -63329 -36629 -55386 -14991 -20580 25440 64756 38883 -19136 22430 -5584 95373 -73506 -66382 12393 -49750 -64219 82970 -93474 62460 -38750 -44065 27270 41494 -91431 -91052 -50149 30713 -34075 -79145 29297 47592 -99977 -34144 9203 37023 -93514 62047 -20094 86081 -50785 -89840 -26270 -57697 98470 95398 -23838 -94583 29238 -81023 84927 36868 -95564 5446 -46612 62950 21963 75617 40815 -62482 -74914 -66328 -11175 -80481 -32956 36248 -47192 -84276 -58137 64286 96457 -16361 -31924
Output  
1 4 4 4 5 8 8 8 9 10 12 12 13 15 15 16 17 18 20 20 21 24 24 24 26 26 28 28 29 30 31 32 36 36 36 36 38 38 40 40 41 43 43 44 46 46 48 48 49 52 52 52 53 54 56 56 57 60 60 60 61 64 64 64 66 66 68 68 69 70
Input  
100 1
-98438 35668 65271 68418 -9767 -37168 -36967 97415 -61935 59082 47844 -76375 93385 -86863 23235 -79183 53924 -57357 -96101 73643 53649 -98398 -59388 54929 -443 32037 54087 -80250 23573 -14931 -58932 66025 89529 24494 -15204 57248 85004 -1301 27512 -45542 -48122 -64896 -51907 -46116 -2040 11516 75989 40392 5682 -99100 55352 12879 -73539 -54865 -58076 -97131 9054 37598 25143 67307 -79734 -73963 25337 72939 -31582 32370 -19739 38157 -44307 65195 -59508 42178 -38032 -2649 -46432 -70445 85705 -57772 4234 51905 12290 -96408 -90519 30647 62308 54927 -28382 -89869 24554 59514 -29014 68769 83201 60334 48776 -3640 41887 67278 25803 -9858  
Output
1 -1 -1 -1 5 6 7 -1 9 -1 -1 12 -1 14 -1 16 -1 18 19 -1 -1 22 23 -1 25 -1 -1 28 -1 30 31 -1 -1 -1 35 -1 -1 38 -1 40 41 42 43 44 45 -1 -1 -1 -1 50 -1 -1 53 54 55 56 -1 -1 -1 -1 61 62 -1 -1 65 -1 67 -1 69 -1 71 -1 73 74 75 76 -1 78 -1 -1 -1 82 83 -1 -1 -1 87 88 -1 -1 91 -1 -1 -1 -1 96 -1 -1 -1 100  
Input 
##  Editorial :
First we will store all the negative indices of array **a** in vector **v**. After every element we print we would increase our count by 1. We will
check whether our negative element lies in range of  starting index of subarray and end index of subarray  
If it lies in range of starting index we would print the index of negative element +1 and update starting and last element of index and
also store the index of vector v 
If not  we will update starting index of subarray and end index of subarray and also print **-1** since wwe did not find any negative element  when our **v** index reaches its limit and we will check for the index +1 that our starting and ending index lies int the range or not and repeat the same processes again. Time complexity
is min **(O(n.k) ,O(n.size of vector))**

  ## Solution 
  ``` C++
  #include <iostream>
#include <bits/stdc++.h>
using namespace std;
 
 
 
int main()
{
  long int n,k;
  cin>>n>>k;
  vector <long int> pos ;



  int pos1 = -1;
  for (int i = 0; i <n; i++)
{
      long int x;
      cin>>x;
      if(x<0){
        pos.push_back(i);
      }
}
   long int start = 0;
long int end = k-1;
long int j = 0;

  long int z;
  long long int counter = 0;
    for (z = 0; z <n-k+1; z++)
{
    if(counter==n-k+1){
  break;
}
    else if(z==pos.size()){
  cout<<-1<<" ";
  counter=counter+1;
  z=pos1;
  start=start+1;
    end=end+1;
  
}
else if((start<=pos[z] && (pos[z]<=end))){
      cout<<pos[z]+1<<" ";
      counter = counter+1;
      z=z-1;
      start=start+1;
    end=end+1;
    pos1 = z;
      

    }

    
    

  

  }
  
  



cout<<endl;




  return 0;
}
```
