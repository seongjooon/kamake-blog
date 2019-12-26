---
title: 'Sorting Algorithm'
date: 2019-8-16 23:13:43
category: 'Data Structure'
---

> #### Where sorting algorithms help us

- Sorting a list of people

- Find the median(중간 값)

- Find duplicates in some data

- Binary Search in a Database

> #### Why do we study sorting algorithms?

- Need guaranteed performance?

  : 시스템 정렬을 쓰면 될텐데, 그럼에도 불구하고 정렬 알고리즘을 사용할 수 있어야 할까?

- Large records? & Small records?

  : (데이터의 양에) 상황에 따라 알고리즘의 로직이 달라질 수 있다.

- Stable?

  :제한사항에 맞는 성능적인 보장이 필요한 경우에 맞춰서 사용해야한다.

> ### Bubble Sort

정렬하는 방식이 버블처럼 점진적으로 자신의 위치를 찾아간다는 것이다. n 개의 원소를 가진 배열을 정렬할 때, In-place sort 로 인접한 두 개의 데이터를 비교해가면서 정렬을 진행하는 방식이다. 가장 큰 값을 배열의 맨 끝에다 이동시키면서 정렬하고자 하는 원소의 개수 만큼을 두 번 반복하게 된다.

#### How it works

- 정렬해야하는 대상이 있는 경우

- 반복적으로 전체를 순회할 경우 바로 옆에 있는 요소와 비교한다.

- 한번의 순회를 할때마다 하나의 요소들이 제 위치를 찾아가는 방식이다.

#### Big-O

- worst case : O(n^2) When does it have worst case perfomence?

- best case : O(n) When does it have worst case perfomence?

#### Disadvantages

성능적으로 떨어진다, 자료가 많아질 수록 빅오의 최악의 상황이 더욱 심화 된다.

#### Advantages

- Memory : **"in place"**(자료안에서 제한적인 상황) 주어진 자료 이외에 추가사항이 없는 데이터

- Easy to write

- Good for testing whether a list is sorted or not : 리스트가 정렬이 돼있는지 아닌지 테스트할 경우

> ### Insertion Sort

방향은 왼쪽 -> 오른쪽이다. 제 자리에 푸쉬해주도록 한다. 현재 인덱스의 왼쪽 원소와 비교한다.

#### Big-O

- worst case : O(n^2)

- best case : O(n) / (버블 정렬과 거의 동일)

#### Disadvantages

성능적으로 좋지 않다. (구리다) 그러나 기본적으로 알아야한다.

#### Advantages

- Memory : **"in place"**(자료안에서 제한적인 상황) 주어진 자료 이외에 추가사항이 없는 데이터

- Easy to write

- Good for testing whether a list is sorted or not : 리스트이 정렬이 돼있는지 아닌지 테스트할 경우
  (버블과 거의 동일)

> ### What does "Stable" mean?

원본 데이터의 두 요소의 **상대적인 위치**가 최종 결과에서도 유지되는가에 따라 stable과 unstable이 결정된다. 상황에 따라 기존의 정보 위치를 유지해야할 경우 있다.
결과적으로 stable한 값을 구해야하는데, 시스템 솔트가 unstable하게 도출한다면 어울리지 않는 기술을 쓰는 것이다.

> ### What does "in place" mean?

Sorts the input without requiring additional space
주어진 데이터 내에서 사용하면 되는 것인지 아닌지에 따라 구분된다.
[Reference link](https://www.quora.com/What-do-you-mean-by-in-place-and-stable-sorting-techniques)

> ### Selection Sort

방향은 왼쪽 -> 오른쪽이다. 인덱스에 있어야하는 요소를 찾아서 바꿔 정렬하는 방법이다. Insertion과 비슷하지만 절대적인 인덱스 기준으로 진행된다. 선택된 원소를 한 번만 바꿔준다. 하지만 여러 번 비교를 하는 것은 마찬가지이다.

#### Big-O

- worst case : O(n^2)

- best case : O(n^2) 자리를 기준으로 정렬하기 때문에 더 나아질 수 있는 자료는 없다.

#### Disadvantages

성능적으로 거의 최악이다. (완전 구려)

#### Advantages

- Memory : "in place"기존 데이터에서 인덱스만 교환한다. 추가 공간의 필요성이 없기 떄문이다.

- Easy to write

##### Is selection sort stable?

**unstable**.

> ### Merge Sort

It is based on the process of merging two sorted arrays into a single sorted array.
병합 정렬.
정렬된 두 배열을 하나의 정렬된 배열로 만드는 방법.

#### Big-O

- worst case, best case: O(n log n) logn으로 진행이 되는데 n개로 되기 때문이다.

#### disadvantages

- in place가 아니다. => 공간적인 필요가 많다. O(n) space.

- n log n은 n^2보다 (항상) 빠르다.

#### Advantages

- Best case, Worst case: All O(n log n)

  다른 정렬의 성능보다 낫다. 베스트나 월스트의 빅오가 같다. 꾸준히 잘하는 선수. (상황에 맞게 쓰면된다.)

  [Reference link](https://www.quora.com/What-are-the-pros-and-cons-of-merge-sort)

#### Divide and Conquer

"분할하여 정복한다"의 원리인 것이다. 말 그대로 복잡한 문제를 복잡하지 않은 문제로 분할하여 정복하는 방법이다. 단 분할(divide)해서 정복했으니 정복(conquer)한 후에는 결합(combine) 의 과정을 거쳐야 한다.

- Divide : Split the array in half, forming two subarrays.
  최대한 작은 모양으로 쪼갠다.

- Conquer : Apply merge sort recursively to the subarrays, stopping when a subarray has a single element. 정렬을 재귀적으로 해결하는 것. (이러한 카테고리를 알고 있으면 좋다.)

Merge Sort는 더이상 나누어지지 않을 때 까지 반으로 분할하다가 더 이상 나누어지지 않은 경우(원소가 하나인 배열일 때)에는 자기 자신, 즉 원소 하나를 반환한다. 원소가 하나인 경우에는 정렬할 필요가 없기 때문이다. 이 때 반환한 값끼리 combine될 때, 비교가 이뤄지며, 비교 결과를 기반으로 정렬되어 임시 배열에 저장된다. 그리고 이 임시 배열에 저장된 순서를 합쳐진 값으로 반환한다. 실제 정렬은 나눈 것을 병합하는 과정에서 이뤄지는 것이다.

[Reference link](https://www.geeksforgeeks.org/divide-and-conquer-algorithm-introduction/)

> ### Quick Sort

Sorting 중 가장 빨라서 Quick 이라는 이름이 붙여졌다. 하지만 Worst Case 에서는 시간복잡도가 O(n^2)가 나올 수 있다.

Quick Sort 도 Divide and Conquer 전략을 사용하여 Sorting 이 이루어진다. Divide 과정에서 pivot이라는 개념이 사용된다. pivot 을 기준으로 좌측은 pivot 으로 설정된 값보다 작은 값이 위치하고, 우측은 큰 값이 위치하도록 partition된다. 이렇게 나뉜 좌, 우측 각각의 배열을 다시 재귀적으로 Quick Sort 를 시키면 또 partition 과정이 적용된다. 주의할 점은 partition 과정에서 pivot 으로 설정된 값은 다음 재귀과정에 포함시키지 않아야 한다. 이미 partition 과정에서 정렬된 자신의 위치를 찾았기 때문이다.

#### Space Complexity Time Complexity

- worst case : O(n^2)

- best case : O(nlogn)

[Reference link](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Algorithm)
