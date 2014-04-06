---
layout: post
disqus_comments: true
date: 2014-04-06 01:44:00 GMT+9
title: AngularJS, grunt, karma, bower, yeoman 설치하기 
---
# Test 환경
Mac OS X Mavericks 10.9.2 

# Yeoman 으로 작업 환경 갖추기
![](http://bwahn.github.io/images/yo-bower-grunt.png)

* yo : [CLI tool for scaffolding out Yeoman projects.](http://yeoman.io/)
* bower : [A package manager for the web]( http://bower.io/ )
* grunt : [The Javascript Task Runner]( http://gruntjs.com/ )
* karma : [Spectacular Test Runner for Javascript]( http://karma-runner.github.io/0.12/index.html )

# Vagrant 환경 구성하기 

* Vagrant file 편집
다음과 같이 파일을 편집한다. 

```
$ cd /project/yo_prj

$ vi Vagrantfile
#
# Vagrantfile
# vi: set ft=ruby :

Vagrant.configure("1") do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.define :yo_web do |yo_web_config|
    yo_web_config.vm.network :hostonly, "192.168.100.10"

    yo_web_config.vm.share_folder "www", "/www", "/project/yo_prj/www"
    yo_web_config.vm.provision :shell, :path => "node-bootstrap.sh"
  end
end
```

## node-bootstrap.sh 편집하기 
(설치 시간이 많이 소요된다.)

```
$ vi node-bootstrap.sh

#!/usr/bin/env bash

# Get root up in here
sudo su

apt-get -y update
apt-get install -y python-software-properties
apt-get install -y subversion curl
apt-get install -y git

add-apt-repository -y ppa:chris-lea/node.js
apt-get -y update
apt-get install -y nodejs
apt-get install -y libfontconfig1

sudo npm install -g yo
sudo npm install -g grunt-cli bower
sudo npm install -g generator-webapp
sudo npm install -g generator-angular
sudo npm install -g generator-karma

sudo gem install compass

echo ""
echo ""
echo ""
echo "=========================================="
echo "$ vagrant ssh"
echo "$ cd /www"
echo "$ mkdir my-yo-project"
echo "$ cd my-yo-project"
echo ""
echo "$ yo angular"
echo "or"
echo "$ yo webapp"
echo ""
echo "$ vi Gruntfile.js"
echo "port: 80"
echo "hostname: '192.168.100.10'"
echo ""
echo "$ sudo grunt serve"
echo ""
echo ""
echo "=========================================="
echo "and check the page : http://192.168.100.10"

```

# yo 명려어 
```
// 애플리케이션 생성
$ yo angular 
$ yo angular:app

// 컨트롤러 생성
$ yo angular:controller myController

// 디렉티브 생성
$ yo angular:directive myDirective

// 필터 생성
$ yo angular:filter myFilter

// 서비스 생성
$ yo angular:service myService
```




# Reference : 
* [getting started with yo]( http://www.youtube.com/watch?feature=player_embedded&v=zBt2g9ekiug )
* [Automating front-end workflow with yeoman, @addyosmani Oct 2013 Tokyo]( https://speakerdeck.com/player/f1dbf1e0220a0131d6a8721ad3458357?slide=95# )
* [AngularJS MTV Meetup: AngularJS + Yeoman (2012-10-9)]( http://www.youtube.com/watch?feature=player_embedded&v=XOmwZopzcTA )
