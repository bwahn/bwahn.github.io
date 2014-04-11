---
layout: post
disqus_comments: true
date: 2014-04-09 17:00:00 GMT+9
title: Contribute code to Chromium
---

# 준비작업

* https://code.google.com/p/chromium/wiki/MacBuildInstructions 를 참고하여 소스코드를 받아 놓고, 빌드까지 한다.


* git 정보 확인 

```
➜  ✗  cd  /chromium/src/chrome/browser

➜  browser git:(master) ✗ pwd
/chromium/src/chrome/browser

➜  browser git:(master) ✗ git remote -v
origin	https://chromium.googlesource.com/chromium/src.git (fetch)
origin	https://chromium.googlesource.com/chromium/src.git (push)
```

* http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml 를 참조해서 문제점 찾아보기

```

➜  base git:(master) ✗ cpplint.py * 

  1 Ignoring DEPS; not a .cc or .h file
  2 Done processing DEPS
  3 Ignoring OWNERS; not a .cc or .h file
  4 Done processing OWNERS
  5 about_flags.cc:44:  "ash/ash_switches.h" already included at about_flags.cc:13  [build/include] [4]
  6 about_flags.cc:103:  Consider using DCHECK_EQ instead of DCHECK(a == b)  [readability/check] [2]
  7 about_flags.cc:460:  { should almost always be at the end of the previous line  [whitespace/braces] [4]
  8 about_flags.cc:467:  { should almost always be at the end of the previous line  [whitespace/braces] [4]
  9 about_flags.cc:479:  { should almost always be at the end of the previous line  [whitespace/braces] [4]
  
```

```
about_flags.cc:44:  "ash/ash_switches.h" already included at about_flags.cc:13  [build/include] [4] 
=> 문제점 리뷰후 내용을 수정 
```

* branch 생성

```
$ git checkout -b base_cleanup

$ git status 

```

* 수정된 내용을 commit

```
$ git commit -am "cleaning the code"
...
```

* AUTHORS에 자신의 이름/이메일 추가한다.

```
➜  src git:(master) ✗  pwd
/chromium/src

➜  src git:(master) ✗  vi AUTHORS
...


```




```

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
