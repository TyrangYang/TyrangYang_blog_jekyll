---
title: All algorithm in C++
categories: STL-study-note
tags: 
    - c++
    - STL
    - algorithm
---

## Content
- [Content](#content)
- [Algorithm Overview](#algorithm-overview)
- [Heap](#heap)
- [Number](#number)
- [Set](#set)
- [Shuffle](#shuffle)
- [Sort](#sort)

## Algorithm Overview

**'*' --> new feature from C++11**

| Algorithm Name | Usage | Mutating? | Head File |
| :---:          | :---: | :---: | :---: |
| [accumulate](#number) | accumulate elements | N | numeric |
| [adjacent_difference](#number) | difference between close elements | Y (if in-place) | numeric|
| adjacent_find | | N | algorithm |
| all_of* | | N | algorithm |
| any_of* | | N | algorithm |
| binary_search | binary search | N | algorithm |
| copy | | Y (if in-place) | algorithm |
| copy_backward | | Y (if in-place) | algorithm |
| copy_if* | | | algorithm |
| copy_n* | | Y (if in-place) | algorithm |
| count | | N | algorithm |
| count_if | | N | algorithm |
| equal | | N | algorithm |
| equal_range | | N | algorithm |
| fill | | Y | algorithm |
| fill_n | | Y | algorithm |
| find | | N | algorithm |
| find_end | | | algorithm |
| find_first_of | | N | algorithm |
| find_if | | N | algorithm |
| find_if_not* | | N | algorithm |
| for_each | | N | algorithm |
| generate | | Y | algorithm |
| generate_n | | Y | algorithm |
| includes | | N | algorithm |
| inplace_merge | | | algorithm |
| inner_product | | N | numeric |
| inplace_merge | | Y | algorithm |
| [iota](#number) | Store increasing sequence | Y | numeric |
| [is_heap*](#heap) | Test if range is heap | N | algorithm |
| [is_heap_until*](#heap) | Find first element not in heap order. | N | algorithm |
| is_partitioned* | | | algorithm |
| is_permutation* | | | algorithm |
| [is_sorted*](#sort) | Check whether range is sorted | N | algorithm |
| [is_sorted_until*](#sort) | Find first unsorted element in range | N | algorithm |
| iter_swap | | Y | algorithm |
| lexicographical_compare | | N | algorithm |
| lower_bond | | N | algorithm |
| [make_heap](#heap) | Make heap from range | Y | algorithm |
| max | | N | algorithm |
| max_element | | N | algorithm |
| merge | | Y (if in-place) | algorithm |
| min | | N | algorithm |
| minmax* | | | algorithm |
| minmax_element* | | | algorithm |
| min_element | | N | algorithm |
| mismatch | | N | algorithm |
| move* | | | algorithm |
| move_backward* | | | algorithm |
| next_permutation | | Y | algorithm |
| none_of* | | | algorithm |
| nth_element | | Y | algorithm |
| [partial_sort](#sort) | Partially sort elements in range while the remaining elements are left without any order | Y | algorithm |
| [partial_sort_copy](#sort) | Copy and partially sort range | Y (if in-place) | algorithm |
| partial_sum | | Y (if in-place) | numeric |
| partition | | Y | algorithm |
| partition_copy* | |  | algorithm |
| partition_point* | | | algorithm |
| [pop_heap](#heap) | Pop element from heap range. Range shrink and value is at end. | Y | algorithm |
| prev_permutation | | Y | algorithm |
| [push_heap](#heap) | Push element into heap range. Range extend | Y | algorithm |
| power | | N | numeric |
| [random_shuffle](#shuffle) | Randomly rearrange elements in range | Y | algorithm |
| remove | | Y | algorithm |
| remove_copy | | Y | algorithm |
| remove_copy_if | | Y | algorithm |
| remove_if | | Y | algorithm |
| replace | | Y | algorithm |
| replace_copy | | Y | algorithm |
| replace_copy_if | | Y | algorithm |
| replace_if | | Y | algorithm |
| reverse | | Y | algorithm |
| reverse_copy | | Y | algorithm |
| rotate | | Y | algorithm |
| rotate_copy | | Y | algorithm |
| search | | N | algorithm |
| search_n | | N | algorithm |
| set_difference | | Y (if in-place) | algorithm |
| set_intersection | | Y (if in-place) | algorithm |
| set_symmetric | | Y (if in-place) | algorithm |
| set_union | | Y (if in-place) | algorithm |
| [shuffle*](#shuffle) | Randomly rearrange elements in range using generator | Y | algorithm |
| [sort](#sort) | Sort elements in range | Y | algorithm |
| [sort_heap](#heap) | Sort elements of heap | Y | algorithm |
| stable_partition | | Y | algorithm |
| [stable_sort](#sort) | Sort elements preserving order of equivalents | Y | algorithm |
| swap | | Y | algorithm |
| swap_ranges | | Y | algorithm |
| transform | | Y | algorithm |
| unique | | Y | algorithm |
| unique_copy | | Y | algorithm |
| upper_bond | | N | algorithm |


## Heap

Heap algorithm need to cooperate with other container usually vector or array.

More detail about heap: [Here]({{site.url}}{{site.baseurl}}/stl-study-note/2019/07/31/containers.html)

```cpp
#include <iostream>
#include <vector>
#include <algorithm> // heap
#include <functional>
using namespace std;

int main(int argc, char const *argv[]){
    int ia[10] = {0,1,2,3,4,5,6,7,8,9};
    vector<int> iv(ia, ia+10);

    //is_heap
    cout << boolalpha;
    cout << is_heap(iv.begin(), iv.end()) << endl; // false

    // make_heap
    make_heap(iv.begin(), iv.end(), greater<int>()); // 0 1 2 3 4 5 6 7 8 9
    cout << is_heap(iv.begin(), iv.end(), greater<int>()) << endl; // true

    make_heap(iv.begin(), iv.end()); // 9 8 6 7 4 5 2 0 3 1
    cout << is_heap(iv.begin(), iv.end()) << endl; // true

    // pop_heap
    pop_heap(iv.begin(), iv.end()); // 8 7 6 3 4 5 2 0 1 9
    cout << iv.back() << endl; // 9
    iv.pop_back();

    // push_heap
    iv.push_back(99);
    push_heap(iv.begin(), iv.end()); // 99 8 6 3 7 5 2 0 1 4

    // sort_heap
    sort_heap(iv.begin(), iv.end()); // 0 1 2 3 4 5 6 7 8 99

    // Base on array
    make_heap(ia, ia + 10); // 9 8 6 7 4 5 2 0 3 1
    pop_heap(ia, ia + 10);

    // is_heap_until
    auto iter = is_heap_until(ia, ia + 10);
    cout << *iter << endl;
    return 0;
}
```

[Back to top](#content)

## Number

```cpp
#include <i>
```

[Back to top](#content)

## Set

[Back to top](#content)

## Shuffle

1. The only difference is that random_shuffle uses *rand()* function to randomize the items, while the shuffle uses *urng* which is a better random generator, though with the particular overload of random_shuffle, we can get the same behavior (as with the shuffle).

2. shuffle is an improvement over random_shuffle, and we should prefer using the former for better results. But shuffle supported from C++11.

[reference](https://www.geeksforgeeks.org/shuffle-vs-random_shuffle-c/)

```cpp
#include <iostream>
#include <vector>
#include <algorithm> // random_shuffle shuffle
#include <numeric> // iota
#include <ctime> // std::time
#include <cstdlib> // rand, srand
#include <random>       // std::default_random_engine
#include <chrono>       // std::chrono::system_clock
using namespace std;

int myrandom(int i) { return rand()%i; }
int main(int argc, char const *argv[])
{
	srand(unsigned(time(0)));
	vector<int> iv(10);
	iota(iv.begin(), iv.end(), 0); // iv: 0 1 2 3 4 5 6 7 8 9

	random_shuffle(iv.begin(), iv.end()); // 6 0 3 5 7 8 4 1 2 9 
	random_shuffle(iv.begin(), iv.end(), myrandom); // It is random, since srand set by time.

	iota(iv.begin(), iv.end(), 0); // iv: 0 1 2 3 4 5 6 7 8 9
	unsigned seed = std::chrono::system_clock::now().time_since_epoch().count();
	shuffle(iv.begin(), iv.end(), std::default_random_engine(seed)); // It is random
	
	return 0;
}
```

[Back to top](#content)

## Sort

sort() in c++ using itrosort which is combine quicksort and heapsort.

stable_sort() using merage sort. When space is enough, the complexity is O(nlogn). Otherwise, it is O(n*logn*logn) since many swapping occur in algorithm.

partial_sort using heapsort.

Something different in java. You can see: [Here]({{site.url}}{{site.baseurl}}/langage-comparison/2019/07/12/langage-comparsion-common-method.html)

```cpp
#include <iostream>
#include <algorithm>
#include <functional>
#include <vector>
#include <utility> //pair
using namespace std;

struct less{
	bool operator() (pair<int,int> i, pair<int,int> j){return( i.first < j.first);}
} less_pair;

int main(int argc, char const *argv[])
{
	int myints[] = {32,71,12,45,26,80,53,33};
	vector<int> iv (myints, myints+8); 

	// is_sort
	cout << boolalpha;
	cout << is_sorted(iv.begin(), iv.end()) << endl;

	// sort
	sort(myints, myints+8); // 12 26 32 33 45 53 71 80 
	cout << is_sorted(myints, myints+8) << endl; // true
	sort(iv.begin(), iv.begin() + 4, greater<int>()); // (71 45 32 12) 26 80 53 33

	// is_sorted_until
	auto iter1 = is_sorted_until(myints, myints+8);
	auto iter2 = is_sorted_until(iv.begin(), iv.end(), greater<int>());
	cout << *iter1 << endl; // ???
	cout << *iter2 << endl; // 26


	// partial_sort
	vector<int> iv2 = {32,71,12,45,26,80,53,33};

	partial_sort(iv2.begin(), iv2.begin() + 4, iv2.end()); 
    // (12 26 32 33) 71 80 53 45
	partial_sort(iv2.begin(), iv2.begin() + 4, iv2.end(), greater<int>()); 
    // (80 71 53 45) 12 26 32 33 

	// partial_sort_copy
	vector<int> res_copy(6);

	partial_sort_copy(iv2.begin(), iv2.end(), res_copy.begin(), res_copy.end());

	// iv2 --> 12 26 32 33 71 80 53 45
	// res_copy --> 12 26 32 33 45 53 

	// stable_sort
	pair<int, int> p1(4, 1); pair<int, int> p2(2, 1); pair<int, int> p3(3, 1);
	pair<int, int> p4(2, 2); pair<int, int> p5(1, 1); pair<int, int> p6(2, 3);

	vector<pair<int, int>> iv3 = {p1, p2, p3, p4, p5, p6};

	stable_sort(iv3.begin(), iv3.end(), less_pair); 
    //(1 1) (2 1) (2 2) (2 3) (3 1) (4 1)

	return 0;
}
```

[Back to top](#content)
