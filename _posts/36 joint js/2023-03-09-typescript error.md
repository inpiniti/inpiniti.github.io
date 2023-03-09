---
title: joint js 정렬
author: JUNG YoungKyun
date: 2023-03-09
category: 36 joint js
layout: post
---

JointJS에서 요소를 정렬하는 방법은 다음과 같습니다.

1. `graph.getCells()` 메서드를 사용하여 그래프 내의 모든 셀을 가져옵니다.

2. 셀을 정렬하려는 축에 따라 정렬 함수를 작성합니다. 예를 들어, x 축에 따라 정렬하려면 다음과 같은 코드를 사용할 수 있습니다.

```
function sortByX(a, b) {
  return a.attributes.position.x - b.attributes.position.x;
}
```
3. 정렬 함수를 `sort()` 메서드에 전달하여 셀을 정렬합니다.

```
var cells = graph.getCells();
cells.sort(sortByX);
```
4. 정렬된 셀의 위치를 업데이트합니다. 예를 들어, x 축에 따라 셀을 정렬하려면 다음과 같은 코드를 사용할 수 있습니다.

```
cells.forEach(function(cell, index) {
  cell.position(index * 100, cell.position().y);
});
```
위의 코드는 x 축을 기준으로 100 픽셀 간격으로 요소를 정렬합니다.

5. 마지막으로, 정렬된 셀의 위치를 그래프에 업데이트합니다.

```
graph.trigger('batch:start');
cells.forEach(function(cell) {
  cell.updatePosition({force: true});
});
graph.trigger('batch:stop');
```
위의 코드는 `updatePosition()` 메서드를 사용하여 셀의 위치를 업데이트하고, `batch:start` 및 `batch:stop` 이벤트를 트리거하여 성능을 향상시킵니다.

JointJS에서는 그래프 요소를 정렬하는 다양한 방법이 있으며, `sortBy()` 메서드를 사용하여 기본적인 정렬 기능을 제공합니다. 또한 `layout` 모듈을 사용하여 더 복잡한 레이아웃을 수행할 수도 있습니다.