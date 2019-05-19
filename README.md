# fire_detection

## 1. 영상 읽어오기.

## 2. 영상 크기가 너무 커서 pryDown 을 사용한다. 높이 너비를 홀수 번째 픽셀 제거.

## 3  createBackgroundSubtractorMOG2 를 사용하여 영상의 배경을 제거한다.
<img width="500" src=https://user-images.githubusercontent.com/33244972/57183884-e3d1e900-6eed-11e9-81b9-5da9430783cc.png>

4. 미디안 블러를 이용하여 소금후추 노이즈를 제거한다.

5. 원본 영상이랑 배경을 제거하고 소금후추 노이즈를 제거한 영상이랑 픽셀단위로 and 한다.
6. bgr 이미지를 hsv 이미지로 변경하고 , 불이랑 비슷한 색을 검출한다.
7. threshold 를 이용하여 127 미만인 것은 다시 제거하는데 이과정에서 빨강옷을 입은 사람들이 제거된다.
8. 그후 적절한 팽창으로 빈곳을 채우고
9. connectedComponentsWithStats 를 사용하여 라벨링한다.
10. area가 100 보다 작으면 잡음이라고 생각하여 무시하고 그것 보다 크면 사격형을 만든다.
11. no_red 즉 0 이 아닌 값이 1000개가 넘개 있으면 count 를 1 증가시키고
12. count 가 100 이상이면 화재를 알린다.
