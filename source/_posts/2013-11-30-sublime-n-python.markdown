---
layout: post
title: "Sublime Text 2 以及 配置Python开发环境"
date: 2013-11-30 21:12
comments: true
categories: 
---
### 1，常规的网上有很多，这里不提了，文章结尾给出的链接中也有提到。
### 2，按tab键跳出括号     //在Default (OSX).sublime-keymap文件里添加
    {
        "keys": ["tab"],
        "command": "move",
        "args": {
            "by": "characters",
            "forward": true
        },
        "context": [{
            "key": "following_text",
            "operator": "regex_contains",
            "operand": "^[)\\]\\>\\'\\\"\\ %>\\}\\;\\,]",
            "match_all": true
        }, {
            "key": "preceding_text",
            "operator": "not_regex_match",
            "operand": "^.*\\{$",
            "match_all": true
        }, {
            "key": "auto_complete_visible",
            "operator": "equal",
            "operand": false
        }]
    }
### 3，shift+enter换行     //在Default (OSX).sublime-keymap文件里添加
    {
        "keys": ["shift+enter"],
        "command": "run_macro_file",
        "args": {
            "file": "Packages/Default/Add Line.sublime-macro"
    }
### 4，添加第三方python path
    打开Browse Package，编辑Packages/Python/Python.sublime-build
    添加如下，将PYTHONPATH的值修改为第三方Python类库的位置   
    "env": {"PYTHONPATH": "/Users/chence/Library/Python/2.7/site-packages/"}
### 5，查看python的build path，从这些path应该很容易能分辨出来那些第三方类库的path
    >>> import sys
    >>> print sys.path
### 6，如需使用Python3
    在Sublime Text 2的菜单选Tools → Build System → New Build System，Sublime Text 2会打开一个新文件“untitled.sublime-build”。把上述Python.sublime-build文件的内容复制粘贴进去，把第2行“cmd”: ["python", "-u", "$file"]中的“python”替换为“/Library/Frameworks/Python.framework/Versions/3.2/bin/python3.2”，保存为Python3，然后在Tools → Build System → Python3就可以了。
### 7，个人最喜欢的
    a，快捷键：super＋D；super+shift+D；super+shift+L；super+p （Mac版本，其他版本均有对应）
    b，一些使用率很高的插件: jsFormat；Reveal in Finder（貌似是自带的）；Copy File Name；Terminal（抱歉下边某参考链接给的一些Python插件都还没来得及用，文章会更新的，谁让是B/S呢:) ）
    c，特性：Multiple Selections（多选编辑，参见http://www.sublimetext.com/）；JSON的配置文件；所见即所得：准确点说应该叫操作即得？（修改配置文件或大部分插件下载完成后即时生效）；众多的插件，且用Python编写
### 8，一点不足
    a，对大文件（如GB级别）的正则搜索请使用vim
    b，对Java的支持还是不如eclipse方便（咦，不是说要配置Python开发环境么。。刚才就感觉是要跑题，好了，那就到这吧，Good Begining）

### 参考
    http://www.sublimetext.com/
    http://code-tech.diandian.com/post/2012-10-15/40039775371
    http://mrsunli.com/2012/subl-python/
    http://cndenis.iteye.com/blog/1776192
