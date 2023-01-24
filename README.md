# Pozalabs_Assignment

## 과제: Music VAE, Groove MIDI Dataset를 이용하여 4마디에 해당하는 드럼 샘플 추출

- 참고논문: "A Hierarchical Latent Vector Model for Learning Long-Term Structure in Music" https://arxiv.org/pdf/1803.05428.pdf
- 참고 Github link : https://github.com/magenta/magenta/tree/main/magenta/models/music_vae
- Groove MIDI 데이터셋 https://magenta.tensorflow.org/datasets/groove


#### Dependency 이슈 : magenta 2.1.0 버전을 설치해야한다는 깃허브 이슈를 참고했습니다. 그렇지만 제가 코랩에서 설치한 2.1.4 버전은 에러가 개선되어 무사히 과제를 진행할 수 있었습니다. 
#### Trouble Shooting: 미디 악보 데이터를 오디오 신호로 변환하는 libfluidsynth1의 에러가 발생해 libfluidsynth2로 재설치하여 과제를 진행했습니다.


데이터셋 설명

- drummer: An anonymous string ID for the drummer of the performance.||
- session:	A string ID for the recording session (unique per drummer).||
- id: A unique string ID for the performance.||
- style:	A string style for the performance formatted as “<primary>/<secondary>”. The primary style comes from the Genre List below.||
- bpm:	An integer tempo in beats per minute for the performance.||
- beat_type:	Either “beat” or “fill”||
- time_signature:	The time signature for the performance formatted as “<numerator>-<denominator>”.||
- midi_filenam:	Relative path to the MIDI file.||
- audio_filename:	Relative path to the WAV file (if present).||
- duration: The float duration in seconds (of the MIDI).||
- split: The predefined split the performance is a part of. One of “train”, “validation”, or “test”.||

  
## VAE란?

AE는 입력값으로 넣은 데이터를 통해 출력값으로 내보낼 한점을 만들지만, VAE는 Input data X를 잘 설명하는 feature를 추출하여 Latent vector z에 담고, 이 Latent vector z를 통해 X와 유사하지만 완전히 새로운 데이터를 생성하는 것을 목표로 합니다. 이때 각 feature가 가우시안 확률분포를 따른다고 가정하고 latent z는각 feature의 평균과 분산값을 나타낸다.  
  
### VAE 모델 구조

<p align="center">
<img src="https://miro.medium.com/max/828/1*5Hx_2zTLXablceCOMpAP-g.webp" width="600" height="400" /> 
</p>
  
- Encoder - BidirectionalLSTM(양방향 LSTM) : input을 latent space로 변환
- Decoder-  Hierarchical Decoder(계층적 디코더) : encoder와 반대로 latent space를 input으로 변환
- latent space(code) : Gaussian 확률분포에 기반한 이상적인 샘플링 벡터들의 집합이라고 이해했다.  이 latent space가 주어져야, decoder는 이를 활용해 data를 generate할 수 있다.
- Counstructor : latent space에서 추출한 이상적인 샘플링 값을 디코더로 보내는 역할.
  
  
### VAE 장단점
- 장점 : 확률 모델을 기반으로 했기 때문에, 잠재 코드를 더 유연하게 계산할 수 있다.
- 단점 : Density를 직접적으로 구한것이 아니기 때문에 Pixel RNN/CNN 과 같이 직접적으로 Density를 구한 모델보다는 성능이 떨어진다.


Music_VAE 논문은 계층적 디코더를 활용하는 반복적인 Variational Autencoder인 Music_VAE를 제안한다. 그들이 만든 계층적 모델이 기준치보다 훨씬 더 나은 성능을 보여준다는 것을 129명의 평가단에게 30초 가량의 16마디 트리오, 드럼, 멜로디 3가지의 마디를 들려 주었을 때 드럼은 실제 데이터보다 더 좋다는 결과를, 보여주었고 나머지 두 개는 일반 flat 샘플보다는 좋다는 평가를 입증했다. 
나는 텐서플로우를 통해 이 모델을 코드로 구현해보았고 내가 만든 샘플도 처음 들었을때는 신기했고 흥미로웠다. 향후 파이토치를 통해서도 구현해보고자 한다. 

## 실제 만든 두 개의 샘플을 깃허브에 첨부했습니다.
