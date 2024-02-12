Replace each element by its rank given in array in C++
In this article, we will brief in on how to replace each element by its rank in the given array using C++ language. There is an array of n elements, replace each element of the array by its corresponding rank. The minimum value element will have the highest rank.

Replace each element of the array by its rank
While loop in C
Here, we will discuss the following methods for replacing the elements by its rank. 

Method 1 : Using Naive approach.
Method 2 : Using Hash-map.
Method 1 :
Create a copy of the given input array.
Sort the copied array.
Run a nested loop and find the position of the given array element in the sorted array.
And replace the element with the position.
Print the modified input array.
Method 1 : Code in C++
#include<bits/stdc++.h>
using namespace std;

int main(){
    int arr[] = { 100, 2, 70, 12 , 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    int temp[n];
    for(int i=0; i<n; i++)
    temp[i] = arr[i];
    
    //sort the copied array
    sort(temp, temp+n);
    
    for(int i=0; i<n; i++){
    
        for(int j=0; j<n; j++){
            if(temp[j]==arr[i])
            {
                arr[i] = j+1;
                break;
            }
        }
    }
    
    for(int i=0; i<n; i++)
    cout<<arr[i]<<" ";
}
Output
5 1 3 2 4
Method 2 :
Copy the given arr[ ].
Then sort that copied array in ascending order.
Then traverse in the copied array and put their rank in Hash Map by taking a rank variable.
If the element is not present then update rank of the element in Hash-Map and increment rank variable as well.
Traverse the given array arr[] assign the rank of each element using the rank stored in Hash Map.
Method 2 : Code in C++
#include 
using namespace std;
 
void changeArr(int input[], int N)
{
    // Copy input array into newArray
    int newArray[N];
    copy(input, input + N, newArray);
 
    sort(newArray, newArray + N);
    int i;
     
    map ranks;
 
    int rank = 1;
 
    for(int index = 0; index < N; index++)
    {
 
        int element = newArray[index];
 
        if (ranks[element] == 0)
        {
            ranks[element] = rank;
            rank++;
        }
    }
 
    for(int index = 0; index < N; index++)
    {
        int element = input[index];
        input[index] = ranks[input[index]];
    }
}
 
// Driver code   
int main()
{
     
    int arr[] = { 100, 2, 70, 12, 90};
 
    int N = sizeof(arr) / sizeof(arr[0]);
     
    // Function call
    changeArr(arr, N);
 
    for(int i = 0; i < N; i++)
    {
        cout << arr[i] << " ";
    }
    
    return 0;
}
Output
5 1 3 2 4
