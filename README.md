# IAM-Emoticon
내가 이모티콘이 된다면? StyleGAN2를 활용한 이모티콘 생성

### Background
오늘날, 남녀노소 가리지 않고 연락을 주고 받을 때, 이모티콘을 사용합니다. </br>
하지만 상황에 맞는 이모티콘과 원하는 이모티콘을 사용하기 위해선 여러 이모티콘을 구매해야합니다. </br>
자신의 감정을 담은 얼굴 사진으로 원하는 애니메이션 캐릭터 그림체로 다양한 감정을 전달해보세요.

![image](https://user-images.githubusercontent.com/103553532/209472015-b0b7c5a3-f436-4819-9479-fde0bcb28d7e.png)

### Use model and library

[이미지 생성] - Stylegan2 (pretrained-model)</br>
[사진 감정 분류] - FER (library)</br>
[감정에 따른 텍스트 생성] - KoGPT2(pretrained-model)

### FLOW
1. 짱구 학습데이터 구축 -> 많은 연령대에서 가장 인기 있는 애니메이션 짱구는 못말려 캐릭터로 이모티콘 생성 (크롤링, 수작업)</br>
2. Pretrained-model(https://github.com/happy-jihye/Cartoon-StyleGAN)로 짱구 데이터 fine-tuning - ffhq(외국인 데이터셋)로 pretrained된 모델 사용
3. 짱구 이미지로 변환하기전 원본 이미지의 감정 분류 (FER) - stylegan2모델을 학습시키는데 많은 시간을 써서 library로 대체
4. 3에서 output으로 나온 감정을 input으로 감정에 따른 텍스트 생성 (KoGPT2) - 감정에 따른 텍스트 데이터셋 구축 후 fine-tuning
5. Opencv로 텍스트와 생성된 짱구이미지 합성

### Limitation
1. 데이터셋(ffhq256)
  - pretrained된 모델이 ffhq256데이터셋으로 외국인 데이터셋으로 학습된 모델을 활용했기 때문에 외국인 이미지에 비해 한국인 이미지를 짱구 이미지로 잘 생성하지 못함.
2. 캐릭터의 단조로운 표정과 특징
  - 짱구 이미지로 학습을 진행했는데 짱구 캐릭터의 경우 표정이 단조롭고 이목구비가 뚜렷하지 않아 특징을 잡아내기 어려워 이미지를 생성하는데 어려움이 있음.
3. 컴퓨팅 파워
  - 데이터셋 학습 과정을 보면 학습을 진행할수록 짱구 이미지를 잘 생성하는 모습을 볼 수 있지만 학습에 필요한 시간과 비용이 한없이 부족했음.
  
### Review
딥러닝 모델을 가져와서 inference는 여러번 해봤지만 처음으로 task를 결정하고 데이터셋 구축부터 fine-tuning까지 진행한 딥러닝 프로젝트 였다.</br>
프로젝트를 진행하면서 이미지가 잘 생성되지 않아 데이터셋 재구축, 파라미터 조정, 새로운 모델 탐색 등 여러가지 시도를 통해서 문제를 해결해 갔다.</br>
ML TASK와 다르게 DL TASK로 다양한 것들을 할 수 있다는 것을 몸소 느낄 수 있었고 DL에 관심을 더 갖을 수 있게 해준 프로젝트 였다.</br>

### 짱구 데이터셋 학습변화
https://user-images.githubusercontent.com/103553532/209736304-db4c2550-bd68-469f-ae99-09d39390fc01.mp4


