## QuickSort

정수를 요소로 갖는 배열을 입력받아 오름차순으로 정렬하여 리턴해야 합니다

## 조건

- number 타입을 요소로 갖는 배열을 리턴해야 합니다.  
- 배열의 요소는 오름차순으로 정렬되어야 합니다.  
- arr[i] <= arr[j] (i < j)

<br/>

|     input     | output |
| :-----------: | :----: |
| [3,  1,  21] | [1,  3,  21] |

<br/>

### Code

```js
const quickSort = function (arr) {
  if (arr.length <= 1) return arr;

  const pivot = arr[0];
  const left = [];
  const right = [];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] <= pivot) left.push(arr[i]);
    else right.push(arr[i]);
  }

  const lSorted = quickSort(left);
  const rSorted = quickSort(right);
  return [...lSorted, pivot, ...rSorted];
};

```

<br />

## 풀이

간단하게 풀이하면 퀵정렬은 피벗이라는 중심점을 기준으로 피벗보다 작다면 왼쪽으로, 크다면 오른쪽으로 정렬시키고  
다시 왼쪽으로 이동된 요소들에 대한 피벗으로 정렬을 시키고, 오른쪽으로 이동된 요소들에 대한 피벗으로 정렬시키는 방법으로 진행하였다. (재귀)

### 수도코드로 보는 작동방식

```js
/**
 *  [1, 2, 43, 100, 21] 1 [] [2, 43, 100, 21] -> [...[], 1, ...[2, 21, 43, 100]] === [1, 2, 21, 43, 100]
 *    [] -> []
 *    [2, 43, 100, 21] 2 [] [43, 100, 21] -> [...[], 2, ...[21, 43, 100]] === [2, 21, 43, 100]
 *      [] -> []
 *      [43, 100, 21] 43 [21] [100] -> [...[21], 43, ...[100]] === [21, 43, 100]
 *          [21] -> [21]
 *          [100] -> [100]
 * 
 * 
 * [] -> pivot을 기준으로 작은 것은 left, 큰 것은 right, 근데 매개변수로 들어온 배열의 길이가 1이하 인 경우 그냥 리턴 (정렬 할 게 없으니까!)
 * 
 * [1,2,3,6,43,45,532]
 */
```
