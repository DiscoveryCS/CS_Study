## Quick Sort

## Contents
1. 퀵 정렬이란?
2. 퀵 정렬 알고리즘 동작 원리
3. python code
4. java code

## 1. 퀵 정렬이란?

- 분할 정복 알고리즘의 하나로, 평균적으로 매우 빠른 수행속도를 자랑하는 정렬 방법

    - n개의 데이터를 정렬할 때, 최악의 경우에는 O(n^2)번의 비교를 수행하고, 평균적으로는 O(nlogn)의 비교를 수행한다.

## 2. 퀵 정렬 알고리즘 동작 원리

- 하나의 리스트에서 피벗(pivot)을 기준으로 두 개의 비균등한 크기로 분할한다.
- 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 한다.

```markdown
1단계 분할(Divide)
- 입력 배열을 피벗을 기준으로 비균등하게 2개의 부분 배열로 분할한다.
- 여기서 피벗을 중심으로 왼쪽은 피벗보다 작은 요소들을 정렬하고, 오른쪽은 피벗보다 큰 요소들을 정렬한다.

2단계 정복(Conquer)
- 부분 배열을 정렬하는데, 부분 배열의 크기가 충분히 작지 않으면 순환 호출을 이용하여 다시 분할 정복 방법을 적용한다.

3단계 결합(Combine)
- 정렬된 부분 배열들을 하나의 배열에 병합한다.
```

### 2-1. 동작 원리

- 전체 배열 리스트 안에서 하나의 원소를 고르는데, 이 원소를 피벗(pivot)이라고 한다.
- 피벗을 기준으로 왼쪽은 값이 피벗보다 작은 값의 원소들이 나열되고, 오른쪽은 피벗보다 큰 값의 원소들이 나열된다.
- 분할된 두 개의 작은 리스트에 대해 재귀적으로 이 과정을 반복한다. 재귀는 리스트의 크기가 0이나 1이 될 때까지 반복한다.

## 3. python code
```python
def quick_sort(arr):
    if len(arr) <= 1:  # 리스트의 길이가 1 이하일 경우, 정렬 완료
        return arr
    
    pivot = arr[len(arr) // 2]  # 중간값을 피벗으로 선택
    left = [x for x in arr if x < pivot]  # 피벗보다 작은 값
    middle = [x for x in arr if x == pivot]  # 피벗과 같은 값
    right = [x for x in arr if x > pivot]  # 피벗보다 큰 값
    
    return quick_sort(left) + middle + quick_sort(right)  # 재귀 호출로 정렬

# 예제 실행
arr = [3, 6, 8, 10, 1, 2, 1]
print(quick_sort(arr))  # [1, 1, 2, 3, 6, 8, 10]
```

## 4. java code
```java
import java.util.ArrayList;
import java.util.List;

public class QuickSort {

    public static List<Integer> quickSort(List<Integer> arr) {
        // 리스트의 길이가 1 이하일 경우, 정렬 완료
        if (arr.size() <= 1) {
            return arr;
        }

        // 중간값을 피벗으로 선택
        int pivot = arr.get(arr.size() / 2);

        // 피벗보다 작은 값, 같은 값, 큰 값을 저장할 리스트
        List<Integer> left = new ArrayList<>();
        List<Integer> middle = new ArrayList<>();
        List<Integer> right = new ArrayList<>();

        // 리스트를 순회하며 분할
        for (int num : arr) {
            if (num < pivot) {
                left.add(num);
            } else if (num == pivot) {
                middle.add(num);
            } else {
                right.add(num);
            }
        }

        // 재귀 호출로 정렬 후 병합
        List<Integer> sorted = new ArrayList<>();
        sorted.addAll(quickSort(left));
        sorted.addAll(middle);
        sorted.addAll(quickSort(right));
        return sorted;
    }

    public static void main(String[] args) {
        List<Integer> arr = List.of(3, 6, 8, 10, 1, 2, 1);
        System.out.println(quickSort(new ArrayList<>(arr))); // [1, 1, 2, 3, 6, 8, 10]
    }
}
```