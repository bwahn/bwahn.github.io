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
Training at local 8.3 hours with 1 node
Training at cloud : 32 min with 20 nodes ( 15x faster )
결국 장비의 싸움이다. 직접 분산 환경에 장비를 구축하지 말고, Google cloud platform 에서 테스트하고 응용해주세요!로 들렸다. 

------------------------------------------------------------------------------

- Docker 환경에서 TensorFlow를 설치하고 응용하기 
- 발표자 : 안병욱
- 발표자료 : http://www.slideshare.net/EricAhn/tensorflow-in-docker
- 데모코드 : https://github.com/bwahn/tensorflow-kr-docker

------------------------------------------------------------------------------

- Tensorflow 모델 디버깅을 위한 팁과 가이드
- 발표자 : 최종욱(서울대학교에서 컴퓨터비전 및 기계학습을 공부하는 학생)
- 발표자료: https://wookayin.github.io/TensorflowKR-2016-talk-debugging
- 관련코드: https://github.com/wookayin/TensorflowKR-2016-talk-debugging

------------------------------------------------------------------------------

- Zen of Numpy 
- 하성주 (서울대학교 컴퓨터공학부 최적화 연구실에서 박사 과정 )
- 발표자료: https://speakerdeck.com/shurain/zen-of-numpy


