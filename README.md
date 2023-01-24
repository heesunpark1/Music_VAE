# Pozalabs_Assignment

## 이 레포지토리는 포자랩스 과제 제출을 위한 레포지토리입니다

과제: Music VAE, Groove MIDI Dataset를 이용하여 4마디에 해당하는 드럼 샘플 추출

- 참고논문: "A Hierarchical Latent Vector Model for Learning Long-Term Structure in Music" https://arxiv.org/pdf/1803.05428.pdf
- 참고 Github link : https://github.com/magenta/magenta/tree/main/magenta/models/music_vae
- Groove MIDI 데이터셋 https://magenta.tensorflow.org/datasets/groove




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

