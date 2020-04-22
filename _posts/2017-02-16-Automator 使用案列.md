---
toc: true
layout: post
description: Automator 使用案列
categories: [software]
title: Automator
comments: true
---

# Automator 使用案列
尽管前端时间爆出Apple撤销了自动化部门，但是automator对于大量重复性生产工作的任务依然有着windows无法达到的优势
##将多份ppt一键转化成pdf
本人是学生，对于许多ppt课件，转换成pdf稍后学习是本人的刚需
在Automator中新建文稿，选择服务，然后如下配置
![屏幕快照 2017-02-16 下午3.25.22](/blog/images/media/14872295946349/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-02-16%20%E4%B8%8B%E5%8D%883.25.22.png)

其中AppleScript代码部分如下：

```AppleScript
on run {input, parameters}    set theOutput to {}    tell application "Microsoft PowerPoint" -- work on version 15.15 or newer        launch        set theDial to start up dialog        set start up dialog to false        repeat with i in input            open i            set pdfPath to my makeNewPath(i)            save active presentation in pdfPath as save as PDF -- save in same folder            close active presentation saving no            set end of theOutput to pdfPath as alias        end repeat        set start up dialog to theDial    end tell    return theOutputend runon makeNewPath(f)    set t to f as string    if t ends with ".pptx" then        return (text 1 thru -5 of t) & "pdf"    else		if t ends with ".ppt" then        	return (text 1 thru -4 of t) & "pdf"		else        	return t & ".pdf"		end if    end ifend makeNewPath
```

保存好以后就可以直接使用了，在选中需要转换的ppt之后，右键-服务-你保存的服务的名字


