## knn k-nearest neighbor

분류에 유용한 알고리즘, 응용하면 추천 기능도 가능 ex)넷플릭스 추천시스템

## 오렌지와 자몽을 분류해보자

<img src="./assets/knn1.jpg" title="" alt="" width="343">

## 분류된 정보가 있고 새로운 과일이 하나를 분류해야 하는 상황

<img src="./assets/knn2.jpg" title="" alt="" width="349">

## 주변에 있는 k개와 비교하여 가장 유사한 과일 선택

k-nearest의 k는 가장 가까운 k개를 의미

<img src="./assets/knn3.jpg" title="" alt="" width="360">

## 

## 여기서는 주변 3개와 비교하여 오렌지-2개, 자몽-1개이므로 문제의 과일을 오렌지라고 판단

<img src="./assets/knn4.jpg" title="" alt="" width="508">

## knn알고리즘은 정확도 100%는 아니지만 모수가 많아질수록 정확도가 올라가고 유사한 것들을 분류할 수 있기 때문에 넷플릭스 같은 추천 서비스에서 많이 사용됨
