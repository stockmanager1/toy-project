한동안 이것 저것 한다고 여기에 관심을 못써서 오늘은 opencv에 대해 지금까지 배운 내용을 다시 돌아보려고 한다.

# 이미지 읽기/쓰기

## url과 image객체를 통해서 열기
```
url = 'https://cdn.pixabay.com/photo/2018/10/01/09/21/pets-3715733_960_720.jpg'

response = requests.get(url)
pic = Image.open(BytesIO(response.content))

pic
```
## rgb로 표현
```
pic_arr
```
3차원으로 표현됨.

## matplotlib으로 출력
```
plt.imshow(pic_arr)
plt.show()
```
matplotlib에서 rgb순서로 출력됨. 하지만 opencv는  bgr순서로 출력한다.

## opencv에서 출력
```
cv2.cvtColor()
```
를 사용해서 색공간을 rgb로 변경가능하다.
```
image = cv2.cvtColor(pic_arr,cv2.COLOR_BGR2RGB)
cv2_imshow(image)
```
## opencv로 이미지 읽기
path, 이미지 파일의 flag값을 인자로 넣어줌

+ cv2.IMREAD_COLOR: 이미지 파일을 Color로 읽어들이고, 투명한 부분은 무시되며, Default 값

+ cv2.IMREAD_GRAYSCALE: 이미지를 Grayscale로 읽음. 실제 이미지 처리시 중간단계로 많이 사용

+ cv2.IMREAD_UNCHANGED: 이미지 파일을 alpha channel (투명도)까지 포함하여 읽어 들임

+ (주의) cv2.imread()는 잘못된 경로로 읽어도 NoneType으로 들어갈 뿐, 오류를 발생하지 않음

+ 근데 코랩은 이걸 원래 지원을 안해서 따로 호출이 필요하다
```
from google.colab.patches import cv2_imshow

cv2_imshow(image)
```
이러면 정상으로 출력된다.

하지만 이걸 다시 matplotlib으로 출력한다면 엉뚱하게 출력된다.
따라서 이걸 써야한다.
```
image_temp = cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
```

그레이 스케일로 바꾼다면 

```
img_gray = cv2.imread('/content/lion.jpg', cv2.IMREAD_GRAYSCALE)
```
를 사용해서 변경한다.

## 이미지 쓰기
```
cv2.imwrite()
```
+ 경로, 이미지 배열을 인자로 받음
```
cv2.imwrite('./random_image.png', random_image)
```
이미지를 정상적으로 저장했다면 true를 출력한다.

|imread|imshow|imwrite|
|------|---|---|
|이미지를 읽고 저장|출력|다른 이름으로 이미지 저장|
