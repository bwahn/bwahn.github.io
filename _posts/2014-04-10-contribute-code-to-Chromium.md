---
layout: post
disqus_comments: true
date: 2014-04-09 17:00:00 GMT+9
title: Contribute code to Chromium
---

# Contribute 하기 

```
	/ git 정보 찾기 
	$ git remote -v

	$ cpplint * >& out.out

	/ 적당한 내용 수정

	// 확인
	$ git status 

	// AUTHORS 에 자신이름 이메일 추가

	// branch 작업
	$ git checkout -b bwahn_cleanup

	// commit
	$ git commit -am "aaaa"

	// codereview사이트로 upload
	// BUG와 TEST를 안해도 되니 모두 NONE 으로..
	$ git cl upload

	// 업로드하면 아래처럼 번호가 나온다.
	https://codereview.chromium.org/232973002/ 

	// 해당 디렉토리에 OWNERS를 지정하기위해 
	// 적당한(되도록 착한) 사람을 선택한다.
	// 
	$ cat OWNERS

	// https://codereview.chromium.org/232973002/ 
	// 에디트 후 review : darin@chromium.org 지정
BUG=NONE
TEST=NONE


	// Publish+Mail Comments 로 메일을 보낸다. 

	// reviewer로 부터 
	// lgtm 커멘트를 받는다. 
```


# Reference : 
* [Contributing Code to Chromium]( http://dev.chromium.org/developers/contributing-code )
