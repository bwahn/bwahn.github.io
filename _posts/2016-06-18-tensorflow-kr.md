---
layout: post
disqus_comments: true
date: 2016-06-18 01:00:00 GMT+9
title: Tensorflow-KR
---

일시: 2016년 6월 18일 11:50AM - 7:00PM

장소: Google Seoul office (역삼역 2번출구 강남 파이낸스 센터 22층)

주최: TensorFlow-KR https://www.facebook.com/groups/TensorFlowKR/ 

후원: 구글 코리아
------------------------------------------------------------------------------

- Machine Intelligence made easy: Vision/Speech API, TensorFlow and Cloud ML  
- Kaz Sato (Staff Developer Advocate, Tech Lead for Data & Analytics, Google Cloud Platform. He  is Staff Developer Advocate at Cloud Platform team, Google Inc. He leads the developer advocacy team for Machine Learning and Data Analytics products, such as TensorFlow, Vision API and BigQuery, and speaking at major events including Google I/O 2016, Strata+Hadoop World 2016 San Jose, Google Next 2015 NYC and Tel Aviv and DevFest Berlin.)
- [발표자료](http://sssslide.com/speakerdeck.com/kazunori279/machine-intelligence-made-easy).

앞부분은 Neural Network 소개, operation 소개를 했다. [playground](http://playground.tensorflow.org/) 를 예를 들어 Classification, Hidden Layer 예를 소개했다. 

Vision/Speech API는 기술 문서나 홍보 자료를 읽어보지 않았었다. Vision Query 데모는 재미있는 요소가 많았다.
[구글의 블로그](https://cloud.google.com/blog/big-data/2016/05/explore-the-galaxy-of-images-with-cloud-vision-api)를 읽어보는 걸 추천한다.

Google Datacenter도 소개했다. Machine Learning은 CPU/GPU가 중요하기 때문에 소개한 것 같다.
Borg에 대해서 언급을 했다. 구글링을 통해서 Borg 자료는 얻을 수 있다. [Borg? (Quora)](https://www.quora.com/What-is-Borg-at-Google) 도 도움이 된다. 발표 자료나 논문을 읽기는 부담스럽다.
Tensorflow와 달리 config file을 borgcfg 모듈로 처리할 수 있다고 한다.

Google Brain이라는 용어도 설명해 주었다. Google Cloud + Neural networks = "Google Brain", Google 을 붙이니 조금 다른 의미처럼 보여진다. 설명하면서 AlphaGo 얘기도 했다.

Google에서 Deep learning을 응용하는 서비스가 의외로 많았다. Maps, Photos, Gmail등인데..... 큰 규모의 서비스 일수록 재미있는 일이 많이 일어나는 것 같다.

TensorFlow가 어디쯤인지 직관적으로 설명을 했다. Academic/research. 테스트하고 문서를 보면서 느꼈는데, 직접 설명을 들을 수 있었다. 응용 서비스에 TensorFlow를 사용하려면 많은 노력이 필요하다. 
슬라이드 중에 Jeff Dean의 Youtube video 데모 소개도 했는데, 

- Training at local 8.3 hours with 1 node
- Training at cloud : 32 min with 20 nodes ( 15x faster )

결국 장비의 싸움이다. 직접 분산 환경에 장비를 구축하지 말고, Google cloud platform 에서 테스트하고 응용해주세요!

------------------------------------------------------------------------------

- Docker 환경에서 TensorFlow를 설치하고 응용하기 
- 발표자 : 안병욱
- 발표자료 : http://www.slideshare.net/EricAhn/tensorflow-in-docker
- 데모코드 : https://github.com/bwahn/tensorflow-kr-docker

키워드는 Docker, GPU, TensorFlow, 분산 환경이였다.
Docker로 TensorFlow를 설치하는 방법을 보여주었다. 
Mac Book에서 주로 테스트하였고, GPU가 동작하는지 보여주기위해 CUDA 설치 방법을 알려주었다.
CUDA 예제 중에서 deviceQuery 를 실행했을때, Mac Book에서 CUDA 오류 메시지를 설명하였다. 
TensorFlow는 Linux Machine(Intel 노트북)+GPU로 공부하거나 연구하는게 정답이다.
사실, Linux Intel notebook + Docker + GPU 테스트 환경이였으면, 좋은 환경이였을 것 같다.

데모는 Mac Book이 호스트이고, Virtual Box에 Ubuntu VM을 설치하였고, VM에 컨테이너를 실행하였다.

TensorFlow를 Google Cloud Platform이 아닌 로컬에서 실행할 수 있는 방법을 찾아서 보여주었다. 
분산 환경에서 TensorFlow를 어떻게 실행할 수 있는지 gRPC, Server 생성, Cluster 설정, Task, Job 의미를 설명했다.
서버 호스트, 포트 정보 설정이 수동이라고 설명했다.
Borg config 모듈같은 기능을 개발해야한다고 설명했다.
분산 디바이스들(여기서는 컨테이너)에게 operator를 할당하는 예제 코드를 보여주었다.

사실, Docker 컨테이너를 생성해서 Jupyter, Tensorboard가 동작하고 result가 저장될지는 확신이 없었고, 
며칠 동안 고민하다가 만들었다.

Demo를 보여주기위해 만든 yaml 파일과 worker, jupyter sample project를 설명했다.
분산 디바이스들은 소스코드에 명시적으로 입력하였다.
gRPC를 위해 모든 디바이스는 8080 포트를 선언하였다.
각 디바이스들은 Mac Book의 /tmp/tf/tensorflow-logs 위치를 컨테이너의 /var/log/tensorflow로 볼륨을 지정하였다.

데모는 Jupyter에서 intro_word2vec_distributed.ipynb 를 불러와서 step 별로 실행하였다. 
word 파일은 30MB가 넘었는데, Mac Book에서 처리하지 못해서 15MB만을 사용했다. 

training이 굉장히 느려서, 2~3 step이후 정지하였고, weavescope에서 worker/ps/master 간에 연결된 그래프를 보여주었다.
연결이 되었다는 의미는 실제 gRPC 통신이 있었다는 것을 의미한다.

마이크, 화면등으로 미숙하게 데모를 진행했지만, meetup 이라 재미있게 즐겼을거라 생각합니다.



------------------------------------------------------------------------------

- Tensorflow 모델 디버깅을 위한 팁과 가이드
- 발표자 : 최종욱(서울대학교에서 컴퓨터비전 및 기계학습을 공부하는 학생)
- 발표자료: https://wookayin.github.io/TensorflowKR-2016-talk-debugging
- 관련코드: https://github.com/wookayin/TensorflowKR-2016-talk-debugging

------------------------------------------------------------------------------

- Zen of Numpy 
- 하성주 (서울대학교 컴퓨터공학부 최적화 연구실에서 박사 과정 )
- 발표자료: https://speakerdeck.com/shurain/zen-of-numpy


