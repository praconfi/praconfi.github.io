---
layout: post
author: "praconfi"
tags: DataStructure
title: "Hash table"
---


# summary
해시테이블은 key와 value가 한 쌍으로 구성된 데이터를 저장한다.  
선형탐색은 데이터량에 비례해서 계산사간이 늘어나게 되는데, 이 문제를 해결해 주는것이 해시테이블이다.  
해시함수(데이터를 고정된 길이의 수치로 변환하는 함수)를 이용해 key의 해시값을 계산하고, 결과값과 매칭되는 배열의 특정 인덱스에 해당 데이터를 저장한다.  
이미 데이터가 저장된 공간에 새로운 데이터가 들어오는 경우 리스트 구조로 기존데이터와 연결한다. 이를 '연쇄법'을 이용한 해시테이블이라 한다.  
해시함수를 이용해 배열 내의 특정 데이터에 빠르게 접근할 수 있다.  
해시테이블에 사용되는 배열의 크기는 너무 작으면 충돌이 많아지고, 선형탐색의 빈도가 높아지게 된다. 반대로 크기가 너무 크면 데이터가 없는 메모리가 많아져서 메모리를 낭비하게 된다.  

|Access| Search|Insert|Delete|   
|:---: | :---: | :---: | :---: |   
| N/A|O(1)|O(1)|O(1)|  

> 단점은 데이터들이 정렬되어 있지 않다는 점이다(python의 hash table인 dictionary는 정렬도 된다고 한다)  

# Hash Table
해시테이블은 해시함수와 함께 데이터 검색을 효율적으로 하기 위해 사용되는 자료구조이다.  
키(key)와 값(value)으로 이루어진 데이터를 해시함수를 이용해 해시값을 얻어 할당된 공간에 저장하는 방식이다.
다른이름으로는 Hash maps, maps, dictionaries, associative arrays라고도 불린다.

## 원리
- 해시테이블에 들어가는 값들은 키(key)와 값(value)로 묶여있다.
- 해싱(Hasing)이란 데이터 관리를 위해, 다양한 길이의 데이터를 고정된 형태의 데이터로 매핑(Mapping)시키는 작업을 뜻한다. 이러한 기능을 구현한 함수를 해시함수 라고 한다.
- 하나의 값을 하나의 키로 저장한다. 두개이상의 다른값을 하나의 키로 저장할 수 없다.
- 생김새가 자바스크립트에 있는 객체(Object)와 비슷하다. 객체도 키와 값을 가지고 있기 때문이다. 하지만 해시테이블은 키를 해시함수를 사용해서 해시값을 만든다는 점이 다르다.

## 사용예시
- `DNS확인 작업`: 웹주소에 대한 IP주소를 할당할 때
- `중복된 항목 방지`: ex) 백신 접종이력 확인
- `캐싱`: 서버의 부하를 줄이기 위해 캐싱을 사용할 때 해당 url이 캐싱되어있느지 해시테이블을 조회한다.

![Untitled (11)](https://user-images.githubusercontent.com/64571546/103440407-778e2680-4c88-11eb-9089-3948d10e2d4c.png)
![Untitled (12)](https://user-images.githubusercontent.com/64571546/103440409-79f08080-4c88-11eb-8e8c-5fad3e3d4d36.png)

## 해시함수의 특징

1. 해시 테이블에서는 주어진 저장소의 크기 만큼의 값(`0`부터 `저장소.length-1`)을 해시값으로 반환해야 한다.
2. 특정한 키를 받으면, 항상 같은 값을 반환해야 한다.
3. 해시 함수 자체는 어떠한 값도 저장하지 않는다. 호출 되었을 때 해시값을 반환하는 역할만 한다.

## 공간할당

유한한 세상에서는 자원을 얼마나 효율적으로 활용하느냐가 중요하다.
마찬가지로 해시테이블을 만들 때 가장먼저 생각해야하는 부분중 하나가 공간할당이다.

해시테이블에 사용하는 배열의 크기가 너무 작으면 충돌이 많아지고, 선형탐색의 빈도가 높아지게 된다. 반대로 크기가 너무 크면 데이터가 없는 공간이 많아져서 메모리를 낭비하게 된다. 적절한 크기설정이 중요하다.

![Untitled (10)](https://user-images.githubusercontent.com/64571546/103440402-72c97280-4c88-11eb-88a7-e624403f9da6.png)

## 해시함수의 충돌
해시 테이블의 단점은 **해시 충돌(hash collision)** 이 발생할 수도 있다는 것이다.
해시 충돌이란 서로 다른 키를 같은 해시값에 대응시키는 것을 의미한다.
아무리 잘 짜인 해시 함수를 사용한다 하더라도, 해시 충돌이 일어날 위험성이 늘 있다.  
### 해결방법
- **(연쇄법)**:  리스트구조로 기존데이터와 연결시킨다.  
  해시 검색시 키값이 일치하지 않는경우 해당 데이터에 연결되어있는 리스트를 순회하면서 조회한다   
- **(개방주소법)**: 충돌이 발생한 경우 다음 후보가 될 주소를 구해서 저장하는 방식이 있다.  
  다음 주소를 구하는 방법에는 해시함수를 여러개 사용하는 방법이나 선형탐사 등 몇가지 방법이 있다.

## 성능
평균적인 경우에 해시테이블은 탐색, 삽입, 삭제 모두 상수시간 O(1)시간이 걸린다. 배열과 연결리스트의 장점만 가져온듯 하다.
하지만 최악의 경우 탐색, 삽입, 삭제 모두 선형시간 O(n)이 걸릴수도 있다.
### 개선법
- `사용률 조정`: 전체데이터공간에서 사용되고있는 공간의 비율이 0.7보다 커지면 리사이징하는것이 좋다.
- `좋은 해시함수`: 전체데이터 공간에 값을 골고루 분포시키는 함수를 사용해야 한다.

## Methods

- `insert(key, value)` - 주어진 키와 값을 저장합니다. 이미 해당 키가 저장되어 있다면 값을 덮어씌웁니다.
- `retrieve(key)` - 주어진 키에 해당하는 값을 반환합니다. 없다면 undefined를 반환합니다.
- `remove(key)` - 주어진 키에 해당하는 값을 삭제하고 값을 반환합니다. 없다면 undefined를 반환합니다.
- `_resize(newBucketNum)` - 해시 테이블의 스토리지 배열을 newBucketNum으로 리사이징하는 함수입니다. 해시 테이블에 저장된 key-value 쌍이 bucketNum의 75%를 넘는 경우 bucketNum을 2배로 늘리고, 25%보다 작아지는 경우 bucketNum을 절반으로 줄입니다. **리사이징 후 저장되어 있던 값을 전부 다시 해싱을 해주어야 합니다.** 구현 후 HashTable 내부에서 사용하시면 됩니다.
  

![_2020-12-23__7 37 11](https://user-images.githubusercontent.com/64571546/103440410-7a891700-4c88-11eb-98fd-7165ecbbb51f.png)
```jsx
const LimitedArray = require('./helpers/limitedArray');
const hashFunction = require('./helpers/hashFunction');
class HashTable {
  constructor() {
    this._itemNum = 0;
    this._bucketNum = 8;
    this._storage = LimitedArray(this._bucketNum);
  }
  insert(key, value) {
    const index = hashFunction(key, this._bucketNum);
    const bucket = this._storage.get(index) || [];
    for (let i = 0; i < bucket.length; i += 1) {
      const tuple = bucket[i];
      if (tuple[0] === key) {
        const oldValue = tuple[1];
        tuple[1] = value;
        return oldValue;
      }
    }
    bucket.push([key, value]);
    this._storage.set(index, bucket);
    this._itemNum += 1;
    if (this._itemNum > this._bucketNum * 0.75) {
      this._resize(this._bucketNum * 2);
    }
    return undefined;
  }
  retrieve(key) {
    const index = hashFunction(key, this._bucketNum);
    const bucket = this._storage.get(index) || [];
    for (let i = 0; i < bucket.length; i += 1) {
      const tuple = bucket[i];
      if (tuple[0] === key) {
        return tuple[1];
      }
    }
    return undefined;
  }
  remove(key) {
    const index = hashFunction(key, this._bucketNum);
    const bucket = this._storage.get(index) || [];
    for (let i = 0; i < bucket.length; i += 1) {
      const tuple = bucket[i];
      if (tuple[0] === key) {
        bucket.splice(i, 1);
        this._itemNum -= 1;
        if (this._itemNum < this._bucketNum * 0.25) {
          this._resize(Math.floor(this._bucketNum / 2));
        }
        return tuple[1];
      }
    }
    return undefined;
  }
  _resize(newBucketNum) {
    const oldStorage = this._storage;
    // min size of 8, return if nothing to do!
    newBucketNum = Math.max(newBucketNum, 8);
    if (newBucketNum === this._bucketNum) {
      return;
    }
    this._bucketNum = newBucketNum;
    this._storage = LimitedArray(this._bucketNum);
    this._itemNum = 0;
    oldStorage.each((bucket) => {
      if (!bucket) {
        return;
      }
      for (let i = 0; i < bucket.length; i += 1) {
        const tuple = bucket[i];
        this.insert(tuple[0], tuple[1]);
      }
    });
  }
}
module.exports = HashTable;
```
- Javascript에서는 {} object가 해시테이블로 pre-built되어있다(python 에서는 dictionary)  
- {}는 key로 string만 할당가능
- Map()은 key로 어떤것이든(obj, array, function)할당 가능하고, 삽입순서대로 정렬되어있다
- Set()은 중복을 허용하지 않는 Javascript의 해시테이블이다

참고 :
- 자바스크립트의 배열은 크기가 제한되어 있지 않은 동적 배열입니다.
배열의 크기를 제한시키기 위해 기본 배열 대신 `part-2/src/helpers/limitedArray`를 사용
- 해시 테이블을 구현할 땐 해시 함수가 필요하다. `part-2/src/helpers/hashFunction`에 미리 준비되어 있는 해시 함수를 사용
- [Hash Table](https://en.wikipedia.org/wiki/Hash_tables)