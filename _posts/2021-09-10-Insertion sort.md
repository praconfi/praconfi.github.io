---
layout: post
title: "Insertion sort"
author: "praconfi"
tags: Algorithm
---

# 삽입정렬

자료 배열의 모든 요소를 왼쪽부터 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘이다.

예시를 보자.

<img src="https://upload.wikimedia.org/wikipedia/commons/e/ea/Insertion_sort_001.PNG">

(a)를 보면, 처음에는 왼쪽 끝의 숫자 3은 정렬이 끝났다고 간주한다. 그리고 두 번째 숫자인 7과 3을 비교한다. 3 < 7 이므로 아무 일도 일어나지 않는다.

(b)에서 회색 처리된 부분을 이미 정렬된 부분으로 간주하고, 오른쪽 미탐색 영역의 첫 번째 숫자 2를 가지고 왼쪽 숫자와 비교한다. 2 < 7 이므로 자리를 바꾸고, 2 < 3 이므로 한 번 더 자리를 바꿔 (c)와 같이 정렬된다.

이런 작업을 모든 숫자가 정렬될 때까지 반복한다.

## 복잡도

n개의 데이터가 있을 때, 최악의 경우

<!-- <pre xml:lang="latex">\sum_{i=1}^{n-1} i = 1 + 2 + 3 + ...  (n - 1)=\frac{n(n-1)}{2}</pre> -->
<img src="https://user-images.githubusercontent.com/62422486/132094130-1bf22a51-bfb6-4ab4-be49-3a1d78fedc2f.png">
번의 비교를 하게 되므로, 시간복잡도는 O(n<sup>2</sup>)

## Ref

[삽입정렬(위키백과)](https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85_%EC%A0%95%EB%A0%AC)
