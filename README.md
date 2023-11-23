# Vector Quicksorting and Duplicate Removal

This C++ program takes a vector as input, performs quicksort to sort the elements, and then removes duplicate values to produce a vector with unique elements. Based on this task:
```plaintext
Implement a program that reads contents of a vector from the standard input.
The program sorts the vector using the quicksort algorithm.
Then the program eliminates all duplicates in the vector,
and stores in the vector only the unique elements.

Example input:
0 3 0 1 4 5 6 5

Example output:
0 1 3 4 5 6
```

## How to Use

1. **Run the Program:** Input a sequence of space-separated integers, followed by Enter.
2. **Output:** - The program will:
     - Sort the input vector using the quicksort algorithm.
     - Remove duplicate elements from the sorted vector.
3. **View Results:** The initial vector provided, sorted vector and the vector with removed duplicates will be printed.

## Example

**Input:**
```plaintext
3 1 4 1 5 9 2 6 5 3 5
```
**Output:**

```plaintext
Given Vector: 3 1 4 1 5 9 2 6 5 3 5

Sorted Vector (using Quicksort): 1 1 2 3 3 4 5 5 5 6 9

Duplicates removed from sorted vector: 1 2 3 4 5 6 9
```
## How it Works

### 1. Input
The program reads a sequence of space-separated integers from the standard input.

### 2. Quicksort
The `quickSort` function is an implementation of the quicksort algorithm, a widely used sorting algorithm with an average time complexity of `O(n log n)`. This algorithm works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot.

#### 2.1. Base Case Check

Before diving into the partitioning process, the function checks if the given partition is valid (i.e., `front >= end`). If not, it returns, as an array with one or zero elements is already sorted.

```cpp
if (front >= end)
{
  return;
}
```
#### 2.2. Partitioning
The `partition` function is called to determine the correct position of the pivot in the sorted array. The pivot is chosen as the first element of the current partition.
The `partition` function is responsible for rearranging the elements in the vector such that elements smaller than the pivot are moved to its left, and elements greater than the pivot are moved to its right.

```cpp
int pivot = vctr[front];
int count = 0; // Number of elements greater than the pivot

for (int i = (front + 1); i <= end; i++)
{
  if (vctr[i] <= pivot)
  {
    count++;
  }
}

int index = front + count; // Position for the pivot
swapVal(vctr, index, front);

int l = front;
int k = end;

// Partition the vector
while (l < index && k > index)
{
  while (vctr[l] <= pivot)
  {
    l++;
  }

  while (vctr[k] > pivot)
  {
    k--;
  }

  if (l < index && k > index)
  {
    swapVal(vctr, l, k);
    l++;
    k--;
  }
}

return index;
```
#### 2.3. Recursive Calls
After the partitioning step, the `quickSort` function is recursively called on the two partitions created by the pivot.

```cpp
int part = partition(vctr, front, end);
quickSort(vctr, front, part - 1);
quickSort(vctr, part + 1, end);
```

This recursive process continues until the base case is reached (when the size of the partition becomes 1 or 0), ensuring that each subarray is sorted.

This approach of recursively sorting partitions is key to the efficiency of quicksort. The algorithm's average-case time complexity of `O(n log n)` makes it a popular choice for various applications where sorting is required.

### 3. Remove Duplicates

The `removeDuplicates` function is responsible for eliminating duplicate elements from a sorted vector, ensuring that the resulting vector contains only unique values.

#### 3.1. **Result Vector Initialization:**
   - A new vector named `result` is initialized to store the unique elements.
   - The first element of the input vector (`vctr`) is added to `result` since it is always unique in a sorted vector.

   ```cpp
   vector<int> result;
   result.push_back(vctr[0]);
   int prev = vctr[0];
   ```  
#### 3.2. **Iterating Through the Vector:**
- A loop is used to iterate through the sorted vector starting from the second element.
- If the current element (`vctr[i]`) is equal to the previous element (`prev`), it is considered a duplicate and not added to the result vector.

```cpp
for (int i = 1; i < vctr.size(); i++)
{
  if (vctr[i] == prev)
  {
    // Duplicate found, do not add to the result vector
  }
  else
  {
    result.push_back(vctr[i]);
  }
  prev = vctr[i];
}
```
#### 3.3. **Updating the Original Vector:**
Finally, the original vector (`vctr`) is updated to contain only the unique elements from the `result` vector.

```cpp
vctr = result;
```

#### Example:
For instance, given the sorted vector `1 1 2 3 3 4 5 5 5 6 9`, the `removeDuplicates` function would transform it to `1 2 3 4 5 6 9`, effectively removing duplicate values.

```cpp
// Remove duplicates from the sorted vector
removeDuplicates(vctr);
cout << "Duplicates removed from sorted vector: ";
print(vctr);
```
The output would be:

```plaintext
Duplicates removed from sorted vector: 1 2 3 4 5 6 9
```
This ensures that the final sorted vector contains only unique elements.

### 4. Display Results
The program prints the original vector, the sorted vector, and the vector with removed duplicates. The results are displayed to the user.
