# Codeforces Rating
                                                                    time limit per test 1 second
                                                                    memory limit per test256 megabytes
                                                                    input standard input
                                                                    output 
Vaibhav was crying in the corner of his room because his rating had dropped again. He notes down his rating changes on Codeforces after every contest. He wants to find out the index of the first rating drop in the array of rating changes for every subarray of size k. He needs your help to do so because his eyes are all watery with tears.  
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
``` 
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
  ## Solution 
  ```
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
