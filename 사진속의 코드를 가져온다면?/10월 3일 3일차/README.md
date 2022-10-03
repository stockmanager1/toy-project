# 10월 03일 개발 3일차
출처 : https://yunwoong.tistory.com/73?category=902345

이걸 보고 느낀게 결국 이걸 하려면 이미지 전처리가 정말 중요하다고 생각되었다.

따라서 이미지 전처리를 할 수 있는 opencv에 대해 좀 둘러볼 필요성을 알게 되어서 오늘부터 opencv를 공부할 예정이다.

공부 자료는 [OpenCV 한번에 끝내기 - 컴퓨터 비전, 이미지 프로세싱의 핵심 라이브러리](https://www.youtube.com/watch?v=XiwA10RfbDk)를 참고했다.

# 오늘 공부한 내용(opencv)

오늘은 주로 OPENCV를 통해서 사진상에 도형을 그리는 것을 중점적으로 배웠다.

그 종류는 직선, 사각, 원, 타원, 다각, 텍스트를 사진상에 그릴 수 있다.

그리고 imwrite코드에 대해 배웠다.

imwrite함수는 이미지 쓰기를 하는 코드라고 배웠는데, 보면 imread함수는 이미지 읽기라고 한다.

그래서 둘의 차이가 잘 이해가 안되었는데 구글링을 해서 감을 잡았다

출처: https://iagreebut.tistory.com/70

imread는 이미지를 읽어오는 함수를 의미하고 이미지의 경로를 저장한 후, 해당 경로에서 이미지를 컬러로 읽어온다.

imread(filename : 이미지 파일 경로 , flag : 이미지를 읽어오는 방식)

imshow()는 imread로 읽어들인 이미지를 파일 윈도우창에 보여준다. 약간 imread와 imshow의 차이를 return과 print의 차이라고 이해했다.

imwrite는 이미지 저장하기로, 어온 이미지를 다른이름으로 저장하는 함수를 의미한다.

imwrite(filename : 이미지를 저장할 경로, image : imread의 리턴 결과)

|imread|imshow|imwrite|
|------|---|---|
|이미지를 읽고 저장|출력|다른 이름으로 이미지 저장|
