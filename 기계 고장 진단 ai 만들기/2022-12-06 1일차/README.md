# 오늘 한것
음성인식에 대한 전반적인 개념 공부

# 음성 인식의 분류
stt(speach to text)--pyaudio, speechrecognition 모듈을 사용한다.

tts(text to speak)-- gtts 모듈을 사용한다.

보통 음성과 관련된 머신러닝은 음성에서 특징값을 추출하고 머신러닝에 적용하는 순서로 이어진다.


# feature extraction
오디오 데이터 = 고차원적이고 주파수로 이루어져 있다. ----> 따라서 이걸 그대로 사용하기 보다는 신호의 성질을 잘 반영하는 feature를 뽑는 편이 좋다.

크게 feature extraction에는 3가지가 존재한다.

1. mfcc
2. mel-spectogram
3. spectrum

보톧 1번 또는 2번에서 많이 고민하는데, 연산량이 적고, 일반적인 학습데이터인 경우에는 mfcc를 사용하고, cnn과 같은 연산량이 많고 특정 도메인의 학습인 경우에는 mel-spectogram이 적합하다.

## mfcc
음성데이터를 특징 벡터화 해주는 알고리즘. 사람이 인지하기 좋은 mel-scale(고주파수를 사람이 인지할 수 있는 주파수로 변형)로 음성데이터를 20~40ms로 쪼개서 fourier transform을 한 것으로 이해하면 됨. 

즉 다시 말하자면, 오디오 신호에서 추출할 수 있는 feature로, 소리의 고유한 특징을 나타내는 수치를 의미한다.
![Screenshot 2022-12-07 at 00 09 03](https://user-images.githubusercontent.com/95357946/205949026-db1268e1-956f-41d4-af7e-213d488a9416.JPG)

이 과정을 하나하나 설명해보자. 
1. audio signal이 windowing을 통해 구간 별로 쪼개진다.

![Screenshot 2022-12-07 at 00 15 58](https://user-images.githubusercontent.com/95357946/205950960-04ba1be2-e482-46eb-8085-886b8192c238.JPG)

여기서 windowing이란 **신호를 구간 값으로 나누어 준것이다.** 하지만 이때 양 끝 값, 즉 경계가 불연속해지면서 신호를 정확하게 받지 못하는 문제가 발생했다. 따라서 양 끝값이 0으로 수렴하는 window function을 각 구간마다 곱해준다. 
![Screenshot 2022-12-07 at 00 16 30](https://user-images.githubusercontent.com/95357946/205950996-9fa87eba-e940-48d3-bad2-27134e663643.JPG)

그러면 이제 각 구간의 끝값이 비슷해진다.

2. fft(faster-fourier transform), 즉 고속 푸리엘 공식을 거쳐 spectrum으로 변한다.

3. 이때 spectrum은 mel filter bank를 통해서 mel-spectrum으로 변한다.
![Screenshot 2022-12-07 at 00 20 28](https://user-images.githubusercontent.com/95357946/205951777-4327c79b-383a-4809-8620-7d2fa6d146f8.JPG)

4. 그리고 cespstral analysis를 통해 mfcc가 도출된다.

![Screenshot 2022-12-07 at 00 21 09](https://user-images.githubusercontent.com/95357946/205951895-1572a827-115b-4903-90d8-40ab7527fd0d.JPG)

각 이 꼭지점이 formant라고 한다. 이것들은 지배적인 주파수의 영역으로, 소리가 공명되는 특정 주파수다.

여기를 잇는 선을 그리는데 이걸 spectral envelope라고 한다.
![Screenshot 2022-12-07 at 00 22 26](https://user-images.githubusercontent.com/95357946/205952218-4460a99c-e628-4318-bcb8-4c0f330bceee.JPG)
여기서 이 포먼트와 엔벨로프를 분리하는 과정에서 우리는 mfcc를 구할 수 있다.

## mel-spectrogram
주파수 특성이 시간에 따라 달라지는 오디오를 분석하기 위한 특징 추출 기법. mel-scale에 기반한 filter bank를 spectrum에 적용하여 도출해낸 것. mel-scale은 filter bank를 나눌때 어떤 간격으로 나누어야 하는지 알려줌.

## spectrum
소리 신호를 주파수와 진폭으로 분석. 고속 푸리에 변환을 적용해서 시간 영역을 주파수 영역으로 변환한다.

# 출차
https://ahnjg.tistory.com/47

https://hyunlee103.tistory.com/54
