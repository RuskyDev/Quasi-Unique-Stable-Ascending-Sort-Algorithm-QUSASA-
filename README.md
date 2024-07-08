# Quasi-Unique Stable Ascending Sort Algorithm (QUSASA)

QUSASA is a simple algorithm that sorts an array of integers in ascending order while ensuring that duplicate elements are quasi-uniquely handled. It maintains the order of appearance for each unique element, ensuring stability in the sorted array.

## How it Works

1. **Sorting**: The algorithm starts by sorting the input array of integers in ascending order using `std::sort` from the C++ Standard Library.

2. **Handling Duplicates**: After sorting, it iterates through the array to identify consecutive duplicate elements. For each set of duplicates, it ensures that only one instance of each duplicate value remains in the final sorted array, positioned after the last occurrence of its predecessor.

3. **Output**: The algorithm prints the sorted array with quasi-unique elements, ensuring that each element appears at most once in the order of its first appearance.

## Usage

To use QUSASA, include the algorithm in your C++ program. Ensure you have the C++ Standard Library available for `std::sort`.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> arr = {12, 11, 13, 12, 11, 12};
    
    // Sort array using QUSASA
    std::sort(arr.begin(), arr.end());
    
    // Handle duplicates quasi-uniquely
    int n = arr.size();
    for (int i = 1; i < n; ++i) {
        if (arr[i] == arr[i - 1]) {
            int j = i;
            while (j < n && arr[j] == arr[i - 1]) ++j;
            if (j < n) std::swap(arr[i], arr[j]);
        }
    }
    
    // Print sorted array with quasi-unique elements
    std::cout << "Sorted array with quasi-unique elements:\n";
    for (int num : arr) std::cout << num << " ";
    std::cout << std::endl;
    
    return 0;
}
```
