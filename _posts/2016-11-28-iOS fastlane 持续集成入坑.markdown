---
layout: post
title:  "iOS fastlane 持续集成"
date:   2016-11-27 23:08:09 -0700
categories: 技术 随笔 生活
tags: 技术
---

    最近学习iOS持续集成,开始打算从jenkins入手,奈何配置太过繁琐插件一直安装失败也就中断了.换个方向从fastlane入手,也是一波三折不过最终成功了.在此记录之.

先记录一下我对fastlane的总体认识.每一个任务(lane)包含四部分
*1.方法描述(desc);
*2.方法名名  (name);
*3.方法参数 (options);
*4.任务体   (task)

eg:

do lane: pgyer do |options|
#todo something
match
gym(schema: bundleName)
deliver
sh "../pgyer.sh options"

end

// 详情参考 : http://icyleaf.com/2016/07/fastlane-in-action/
首先用homebrew安装fastlane(sudo gem install fastlane),当执行fastlane init 是报错 Connect error TSL - peer.开始以为是openssl版本过低,升级openssl(http://blog.csdn.net/pz0605/article/details/51954868),升级后不行!
后来以为是ruby版本和fastlane版本没有对应上,安装rvm下载对应的ruby版本还是不行.
然后百度谷歌各种搜,经过一番努力总算是在万能的Github上早到了解决办法(擦,忘了那个链接下次补上).总之安装后执行fastlane init顺利生成了Fastfile,Appfile等文件.

最后写了一个测试上传蒲公英的脚本自动化打包上传了蒲公英.折腾了一两天最后发现这个其实不难,只不过不会ruby(貌似一个脚本语言都不精通 尴尬).碰上一个小问题都要搜半天.比如
*1.写蒲公英上传脚本时 file=@{filePath}.等号前后不能有空格

还有一个要解决的问题: 执行脚本后ipa包比正常的要大.

今天只是基本会用这个工具,有几个细节还需整理最终熟练运用减少这些繁琐的体力活.

问题:
*1.打包后IPA比正常的大
*2.还没正式测试上传到AppStore





