---
date: 2020-05-27
title: "Flutter Container"
template: post
thumbnail: "../thumbnails/flutter.jpg"
slug: flutter-container
categories:
  - Flutter
tags:
  - blog
  - container
  - basic
---

[![Deno Configuration](https://img.youtube.com/vi/KxgPxG5tfxw/0.jpg)](https://www.youtube.com/watch?v=KxgPxG5tfxw)

Hello everyone, iam fiaz luthfi and now you are on devindo youtube channel. You know flutter has container, but many of us, don't know what can we do more about this countainer. So we talk about this in deep 

This is basic flutter project, you can be done to create this by do ‘flutter create name_project in your command line.

And this is basic of container, and i have set child text is devindo
```bash
Container(
    child: Text('Devindo')
)
```

First one we talk about color in container, inside container you can set color basic
```bash
color: Colors.blue
// also you can change color opacity by do
color: Colors:blue[500] // the code you can see when you do hover
// if you want to use theme color you can do
color: Theme.of(context).accentColor
// but if you have your code color you can covert it to hex and do like this to implement
color: Color(0xff303960) // dark blue
```
next we talk about padding and margin, if you don't know, margin is empty space to surround child.
padding is empty space to inscribe child. to clearly, i try to make it

i create another one container and i set collor as green
first container i set padding for all is 100.0, before continue, we will talk more about this EdgeInsets,

in this widget you have many option to set it, first .all is space all around this widget. but if you only set top only, or bottom, or left or right, you can do .only in this option has 4 option to set space. next is .symetric is option, create space horizontal or vertical, last is .fromWindowPadding, this is to create padding and set pixel ratio as widget, exampe i have padding 100 and pixel ratio is 1.1, so will come like this. 

actualy edgeinserts have option lerp, but it is not be use in basic, this option can be use if we create something like animation. Want to explore about animation? please give a comment

next we talk about margin, berofe padding will make space inside, margin is the opposite, when we set padding, this option will make space inside this box, so if you want set space ouside, just implement margin.

alignment, this option will make child inside container move as you want, example choose postition bottomRight or another you can see this list. but this we not see the effect you can comment for padding to see how alignment is work 

height and width this option will make size of container, you can set with double value, example hight 30, and width 100, or make it relative wih MediaQuery.of(). and set as you want. 

clipBehavour this option will make your widget looks good example if you draw triangle, clipbeavhour will take effect of peformance, for detail you can read this article by [raouf rahicle](https://medium.com/flutter-community/clipping-in-flutter-e9eaa6b1721a)

constraints, this option it to make default size of your child widget, we not talk detail about this, cause this option has many option. example you can set BoxConstain with minimum hight is 100.0. but easily this option will work if you not set exacly number for hight or widhth before, exampe i will comment for hight and set max hight is 300.0

next is decoration also for this option has many option, for exampe i want to set his container have a line border with red color, so you can set boxdecoration and border.all( colors: Colors.black, witdh:10), this will became error because we have set color ouside box, so this color must inside here. also for this option you can set for border radius, or set image as backround, gradient, background blendmode to blend color of this decoration, also you can set of shape.

last we talk about transfrom, this option is to apply matrix before paint container. example i want rotate this container in z direction so you can do Matrix4.rotationZ(0.1) this valu has minimum is zero and maximum is one

that it about container in flutter i hope this video help you understand more about this widget, and please give me comment. Don't forget to subscribe.

Thanks