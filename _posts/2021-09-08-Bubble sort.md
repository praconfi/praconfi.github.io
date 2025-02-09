---
layout: post
title: "Bubble sort"
author: "praconfi"
tags: Algorithm
---

# 버블정렬

오른쪽부터 시작해 왼쪽으로 인접한 두 원소를 비교해가며 정렬하는 방법이다. 시간 복잡도가 O(n<sup>2</sup>)으로 느리지만, 코드가 단순해서 자주 사용된다.

  <div align="center" style="font-size:20px; text-align:center; letter-spacing:10px;">4 2 1 5 3 <U>8</U> <U>6</U></div>

먼저, 오른쪽의 두 수를 비교한다. 오른쪽 숫자가 작으면 왼쪽과 바꾼다.

  <div align="center" style="font-size:20px; text-align:center; letter-spacing:10px;">4 2 1 5 <U>3</U> <U>6</U> 8</div>
그 후 왼쪽으로 한 칸 이동해서 같은 방법으로 두 수를 비교한다. 위 예에서는 오른쪽 숫자가 크므로 자리는 바꾸지 않는다.
  <div align="center" style="font-size:20px; text-align:center; letter-spacing:10px;">4 2 1 <U>5</U> <U>3</U> 6 8</div>
다시 한칸 왼쪽으로 이동해서 같은 방식으로 비교하며, 왼쪽 끝까지 이런 작업을 반복한다.

  <div align="center" style="font-size:20px; text-align:center; letter-spacing:10px;"><mark>1</mark> 4 2 3 5 6 8</div>
  결과는 이렇게 된다. 오른쪽 부터 인접한 두 수를 비교하며 자리를 바꾸다보니 가장 작은 숫자가 왼쪽 끝에 자리하게 됬다. 첫 번째 라운드에서 왼쪽 끝의 숫자는 정렬이 끝났다고 볼 수 있다.<br><br>

이제는 두 번째 라운드다. 다시 오른쪽 끝에서 부터 시작해, 이미 정렬이 끝난 왼쪽 첫 번째 숫자를 제외하고 두 번째 숫자까지 위 작업을 반복한다.

최종적으로 아래와 같이 정렬된다.

  <div align="center" style="font-size:20px; text-align:center; letter-spacing:10px;">1 2 3 4 5 6 8</div>

## 구현

```js
function bubbleSort(array) {
  let lastIndex = array.length - 1;
  // 배열의 마지막 요소의 인덱스 번호 lastIndex를 구한다
  for (let i = 0; i < lastIndex; i++) {
    // 한 라운드가 끝날 때마다 왼쪽 끝부터 정렬이 완료되므로, 왼쪽부터 하 칸씩 오른쪽으로 옮기며 비교 대상에서 제외하기 위한 코드
    for (let j = lastIndex; j > i; j--) {
      // 매 라운드마다 실행될 코드, 오른쪽 끝에서 시작해서 인접한 두 요소를 비교하며 오른쪽 숫자가 작으면 자리를 바꾼다
      if (array[j - 1] > array[j]) {
        let temp = array[j - 1];
        array[j - 1] = array[j];
        array[j] = temp;
      }
    }
  }
  return array;
  // 정렬된 배열을 반환한다
}
```
