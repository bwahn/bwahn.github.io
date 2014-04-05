---
layout: post
disqus_comments: true
date: 2014-04-06 01:44:00 GMT+9
title: AngularJS, grunt, karma bower yeoman
---

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
    yo_web_config.vm.network :forwarded_port, guest: 8080, host: 8080, auto_correct: true

    yard_web_config.vm.share_folder "www", "/www", "/project/yo_prj/www"
    yard_web_config.vm.provision :shell, :path => "node-bootstrap.sh"
  end
end
```

## node-bootstrap.sh 편집하기 
