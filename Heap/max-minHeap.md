# Heap Sort (Max & Min) – Complete Guide

## ✅ Simple Working C++ Code

```cpp
#include <iostream>
using namespace std;

class Heap
{
public:
    int arr[10];

    void input(int n);
    void print(int arr[], int n);
    void maxHeapify(int arr[], int n, int i);
    void minHeapify(int arr[], int n, int i);
    void maxHeapSort(int arr[], int n);
    void minHeapSort(int arr[], int n);
};

void Heap::input(int n)
{
    for (int i = 0; i < n; i++)
        cin >> arr[i];
}

void Heap::print(int arr[], int n)
{
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

// MAX HEAPIFY
void Heap::maxHeapify(int arr[], int n, int i)
{
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest])
        largest = left;

    if (right < n && arr[right] > arr[largest])
        largest = right;

    if (largest != i)
    {
        swap(arr[i], arr[largest]);
        maxHeapify(arr, n, largest);
    }
}

// MIN HEAPIFY
void Heap::minHeapify(int arr[], int n, int i)
{
    int smallest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] < arr[smallest])
        smallest = left;

    if (right < n && arr[right] < arr[smallest])
        smallest = right;

    if (smallest != i)
    {
        swap(arr[i], arr[smallest]);
        minHeapify(arr, n, smallest);
    }
}

// MAX HEAP SORT (Ascending)
void Heap::maxHeapSort(int arr[], int n)
{
    for (int i = n / 2 - 1; i >= 0; i--)
        maxHeapify(arr, n, i);

    for (int i = n - 1; i > 0; i--)
    {
        swap(arr[0], arr[i]);
        maxHeapify(arr, i, 0);
    }
}

// MIN HEAP SORT (Descending)
void Heap::minHeapSort(int arr[], int n)
{
    for (int i = n / 2 - 1; i >= 0; i--)
        minHeapify(arr, n, i);

    for (int i = n - 1; i > 0; i--)
    {
        swap(arr[0], arr[i]);
        minHeapify(arr, i, 0);
    }
}

int main()
{
    Heap h;
    int n;

    cout << "Enter size: ";
    cin >> n;

    cout << "Enter elements: ";
    h.input(n);

    cout << "Original: ";
    h.print(h.arr, n);

    h.maxHeapSort(h.arr, n);
    cout << "Sorted Ascending (Max Heap): ";
    h.print(h.arr, n);

    h.minHeapSort(h.arr, n);
    cout << "Sorted Descending (Min Heap): ";
    h.print(h.arr, n);

    return 0;
}
```

---

# 🧠 Concept Visualization

## 1. Array to Tree Mapping

Index relation:

```
Parent = i
Left   = 2*i + 1
Right  = 2*i + 2
```

Example array:

```
[10, 5, 20, 2, 8]
```

Tree form:

```
        10
       /  \
      5    20
     / \
    2   8
```

---

## 2. Max Heap Rule

👉 Parent must be **greater than children**

```
        20
       /  \
     10    15
```

---

## 3. Min Heap Rule

👉 Parent must be **smaller than children**

```
        2
       / \
      5   8
```

---

## 4. Heapify Intuition

### Max Heapify

* Compare parent with children
* Swap with **largest**
* Repeat recursively

### Min Heapify

* Compare parent with children
* Swap with **smallest**
* Repeat recursively

---

## 5. Heap Sort Flow

### Step 1: Build Heap

Convert array into heap

### Step 2: Extract Root

* Swap root with last element
* Reduce heap size
* Heapify again

---

## 6. Example (Max Heap Sort)

Array:

```
[4, 10, 3, 5, 1]
```

Build max heap:

```
[10, 5, 3, 4, 1]
```

Step swaps:

```
[1, 5, 3, 4, 10]
[5, 4, 3, 1, 10]
...
```

Final:

```
[1, 3, 4, 5, 10]
```

---

## 7. Variable Naming (Simple Mapping)

| Variable | Meaning              |
| -------- | -------------------- |
| i        | current index        |
| left     | left child           |
| right    | right child          |
| largest  | biggest value index  |
| smallest | smallest value index |
| n        | size of heap         |

---

## 🎯 Key Understanding Tips

* Think of array as **tree**
* Always fix from **bottom → top**
* Heapify = "fix subtree"
* Sorting = "extract root repeatedly"

---

If you want next:
👉 I can create step-by-step animation slides for your PPT
👉 Or viva-ready explanation answers
