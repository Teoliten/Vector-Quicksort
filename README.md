# Vector Quicksorting and Duplicate Removal

This C++ program takes a vector as input, performs quicksort to sort the elements, and then removes duplicate values to produce a vector with unique elements.

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
The `quickSort` function is used to sort the input vector in ascending order. It employs the quicksort algorithm, recursively partitioning the vector based on a pivot element.

### 3. Remove Duplicates
The `removeDuplicates` function removes duplicate elements from the sorted vector, keeping only the unique values.

### 4. Display Results
The program prints the original vector, the sorted vector, and the vector with removed duplicates. The results are displayed to the user.
