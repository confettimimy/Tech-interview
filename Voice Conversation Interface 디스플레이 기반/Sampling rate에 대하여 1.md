# 샘플링 레이트

[출처](https://blog.naver.com/satusfree5/220623885225)

### Sample Rate란?

**1초당 들리는 sample갯수를 단위로 나타낸 것**

​    

보통 음악 작업에 사용되는 Sample Rate는 44,100Hz이다.

이 말은 우리의 귀에 1초에 44,100개의 Audio Sample들이 들린다는 얘기이고,

우리가 보통 음악 앱에서 듣는 음원들은 사실 1초에 44,100개의 끊어진 Audio조각들을 엄청난 속도로 들려주는 것이다.

나의 귀는 하나의 연결된 음원이라 착각하는 것.

​    

높은 품질을 위해  높은 Sample Rate가 요구된다.

---

- X3-120 : 장치의 샘플링레이트가 120Hz

- Apogee Mic 96K : 포터블 기기임에도 96kHz까지 Recording이 가능함을 광고. 제품.

​    

<결론>

즉, 당시 샘플링레이트 오류가 났던 것은

오디오 장치가 바뀌었고, **장치마다 지원되는 샘플링레이트가 달라서** 발생했을거라 판단이 된다. (마이크 스피커 장치도 계속해서 바꿨으니, 해당 장치가 해당 샘플링레이트만 지원했을지도)

즉 예를들어 A장치의 샘플링레이트가 44.1kHz이라면,

해당 A장치는 1초에 44,100개의 Audio Sample들을 출력시킨다는 얘기.

(사용했던 시선추적 장치와 같은 맥락으로 생각하면 된다!!)

​    

<면접회상>

그때 PC -> 라즈베리파이로 옮겨서 생긴 문제가 아니라

사용된 오디오 장치가 달라 발생했던 것일 것이다.

라즈베리파이 출력장치 스피커가 달라서(?)

-장치 및 환경마다 샘플링레이트를 다르게 조정해야한다는 사실을 모르고-

---

**음성 파일 정보** 
\- 저장 형태: FLAC (Free Lossless Audio Codec)
\- 채널: 모노
\- 샘플레이트: 44100 Hz
\- 비트레이트: 705 kb/s

​    

~~파일 -> 44100

오디오파일마다에도 샘플링레이트 정보가 있다.

= 해당 오디오 파일이  1초에 44100 오디오샘플 출력시킨다는 뜻.

---

How to obtain the highest sample rate possible in Raspbery Pi using a ADC?

I am working in a project using Raspberry Pi 3 B where I get data from a IR sensor(Sharp GP2Y0A21YK0F) through a ADC MPC3008 and display it in real-time using PyQtgraph library.

​    

This kind of Sampling rate is not achievable with a general-purpose computer like Raspberry Pi, especially with `MCP3008`. The reason being the MCP series of ADC's tops out at `~2.7Mhz` SPI clock at `5V`.

In order to read at `200KHz` rate, you would need a dedicated board.

​    

라즈베리파이와 같은 보통 컴퓨터에서는  그렇게 높은 샘플링레이트를 실현할 수 없다. 즉, 라즈베리파이에서는 일정 주파수까지만 지원해준다.(여기서는 44100)

​    

프로젝트에서는 16000 -> 44100으로 변경해 사용해서

라즈베리파이는 여기까지 지원해주는데 그 초과를 사용해 오류가 났던 건 아닌 것 같고,

사용된 스피커 장치나 오디오장치가 바뀌어서 그런것 같다.

당시 터틀봇에 끼울 마이크랑 스피커를 또샀었다. 기존께 맞지않아서

---



​     

​     

​     

​     

​     

​     

​     

​     

​     

​     

---

### 샘플링 레이트(주파수 범위)    [출처](https://cloud.google.com/solutions/media-entertainment/optimizing-audio-files-for-speech-to-text?hl=ko#sample_rate_frequency_range)

**샘플링 레이트는 오디오 파일의 주파수 범위를 결정합니다. 오디오 파일을 구성하는 초당 샘플 수가 기준이 됩니다. 일반적으로 디지털 오디오 파일의 재생 가능한 최고 주파수는 샘플링 레이트의 절반과 같습니다. 예를 들어 44.1kHz 오디오 파일에서 재생할 수 있는 가장 높은 주파수는 약 22kHz**로, 일반적인 청취자의 가청 주파수 응답 범위의 최상단에 있거나 이를 넘습니다.

전화 및 전기 통신의 샘플링 레이트는 일반적으로 8kHz~16kHz 범위입니다. 이 가이드에서는 일반적으로 16kHz보다 높은 미디어 및 엔터테인먼트 산업과 관련된 형식을 주로 다룹니다. 전화 및 기타 사운드 애플리케이션에 대한 자세한 내용은 [고급 모델로 전화 오디오 텍스트 변환](https://cloud.google.com/speech-to-text/docs/phone-model?hl=ko)을 참조하세요.

_Speech-to-Text를 통한 텍스트 변환에 사용하는 오디오 파일의 샘플링 레이트는 16kHz 이상이 좋습니다._ **오디오 파일에서 볼 수 있는 샘플링 레이트는 일반적으로 16kHz, 32kHz, 44.1kHz, 48kHz입니다.** 특히 높은 주파수에서는 명료도가 주파수 범위에 크게 영향을 받기 때문에 16kHz 미만의 샘플링 레이트에서는 8kHz 이상에 정보가 거의 없거나 전혀 없는 오디오 파일이 생성됩니다. 이 경우 Speech-to-Text가 음성 오디오를 텍스트로 올바로 변환하지 못할 수 있습니다. 음성 명료도에는 2kHz~4kHz 범위 전체의 정보가 필요하지만 이보다 높은 범위의 주파수의 배음(배수)도 음성 명료도를 보존하는 데 중요합니다. 따라서 샘플링 레이트를 최소한 16kHz로 유지하는 것이 좋습니다.

**샘플링 레이트를 변환할 수도 있습니다.** 하지만 오디오 업샘플링은 장점이 없는데, 주파수 범위 정보가 낮은 샘플링 레이트에 의해 제한되고 더 높은 샘플링 레이트로 변환해도 복구할 수 없기 때문입니다. 즉, 8kHz에서 44.1kHz로 업샘플링하면 재생 가능 주파수 범위는 낮은 샘플링 레이트의 절반인 약 4kHz로 제한됩니다. 이 가이드에서는 직접 차이를 듣고 알 수 있도록 다양한 샘플링 레이트와 비트 깊이로 녹음된 오디오 파일을 듣습니다.

---

### 오디오   [출처](https://ko.wikipedia.org/wiki/%EC%83%98%ED%94%8C%EB%A7%81_%EB%A0%88%EC%9D%B4%ED%8A%B8)

**디지털 오디오에서 주로 사용되는 샘플링 레이트는 44.1 kHz, 48 kHz, 88.2 kHz, 96 kHz, 192 kHz이다. 낮은 샘플링 레이트를 사용하면 데이터 크기가 낮아지고 저장과 전송이 용이하다는 장점이 있다. 나이키스트-섀넌 정리에 따르면, 약 50 kHz에서 60 kHz 사이 이상의 샘플링 레이트는 인간이 들을 수 있는 정보를 제공하지 못한다.** 초기 전문 오디오 장비 제조사들은 이러한 이유에서 50 kHz 영역의 샘플링 레이트를 채택하였다. 현대 전문 오디오 장비에는 44.1 kHz, 48 kHz와 더불어 88.2 kHz와 96 kHz가 자주 사용된다. 192 kHz 같은 높은 샘플링 레이트는 상호 변조 왜곡으로 인한 초음파 아티팩트, 너무 빠른 속도로 인한 부정확한 샘플링을 일으키기 쉽다. 미국음향기술자협회는 **대부분의 소프트웨어에 48 kHz의 샘플링 레이트를 권장**하지만, CD와 다른 소비자 용도에 44.1 kHz, 전송 관련 소프트웨어에 32 kHz, 높은 대역폭 또는 완화된 안티 앨리어싱 필터링에 96 kHz를 인정하고 있다.

모든 주요 샘플링 레이트 목록은 다음과 같다:

<IMG SRC="../source/샘플링레이트 표.PNG">

