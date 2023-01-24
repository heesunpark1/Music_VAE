# Pozalabs_Assignment

# 이 레포지토리는 포자랩스 과제 제출을 위한 레포지토리입니다

과제: Music VAE, Groove MIDI Dataset를 이용하여 4마디에 해당하는 드럼 샘플 추출

- 참고논문: "A Hierarchical Latent Vector Model for Learning Long-Term Structure in Music" https://arxiv.org/pdf/1803.05428.pdf
- 참고 Github link : https://github.com/magenta/magenta/tree/main/magenta/models/music_vae
- Groove MIDI 데이터셋 https://magenta.tensorflow.org/datasets/groove


#### Dependency 이슈 : magenta 2.1.0 버전을 설치해야한다는 깃허브 이슈를 참고했습니다. 그렇지만 제가 코랩에서 설치한 2.1.4 버전은 에러가 개선되어 무사히 과제를 진행할 수 있었습니다. 
#### Trouble Shooting: 미디 악보 데이터를 오디오 신호로 변환하는 libfluidsynth1의 에러가 발생해 libfluidsynth2로 재설치하여 과제를 진행


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
  
  
## 모델 구조

<p align="center">
<img src="https://miro.medium.com/max/828/1*5Hx_2zTLXablceCOMpAP-g.webp" width="600" height="400" /> 
</p>
  
Encoder - BidirectionalLSTM(양방향 LSTM) : input을 latent space로 변환

Decodef -  Hierarchical Decoder(계층적 디코더) : encoder와 반대로 latent space를 input으로 변환
latent space(


