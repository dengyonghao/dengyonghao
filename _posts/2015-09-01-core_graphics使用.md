---
layout: post
date: 2015-09-01 15:01:13
comments: true
---
#core graphics使用
##五步曲
###1. 获取上下文

	CGContextRef context = UIGraphicsGetCurrentContext();//获取上下文
	
###2. 创建路径并添加到上下文中

	CGMutablePathRef path = CGPathCreateMutable();//创建路径

###3. 进行绘图内容的设置

	CGPathMoveToPoint(path, nil, 50, 50);//设置路径起点
	CGPathAddLineToPoint(path, nil, 50, 100);//绘制直线(可以根据实际情况选择)
    CGContextAddPath(context, path);//把路径添加到上下文中

    //设置图形上下文状态属性
    CGContextSetRGBStrokeColor(context, 1.0, 0, 0, 1);//设置笔触颜色
    CGContextSetRGBFillColor(context, 0, 1.0, 0, 1);//设置填充色
    CGContextSetLineWidth(context, 1.0);//设置线条宽度
    CGContextSetLineCap(context, kCGLineCapRound);//设置顶点样式
    CGContextSetLineJoin(context, kCGLineJoinRound);//设置连接点样式
    CGContextSetShadowWithColor(context, CGSizeMake(0, 0), 3, [UIColor blackColor].CGColor);//设置阴影(详细参数查看api解释)
	......
	
###4. 开始绘图（CGContextDrawPath）

	CGContextDrawPath(context, kCGPathFillStroke);//最后一个参数是填充类型
	
###5. 释放路径（CGPathRelease）

	CGPathRelease(path);//不在ARC的管理范围之内
