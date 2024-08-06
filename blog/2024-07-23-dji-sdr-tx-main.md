---
slug: teardown/dji-sdr-tx
title: DJI SDR Transmission TX Teardown
authors: [kelvin,treee]
tags: [DJI]
---
北京时间2024年7月17日，DJI发布了全新的SDR图传。根据其官方描述其图传使用软件定义无线电技术，为了一探究竟，我们第一时间从官方购买并进行了详细拆解。

{/*
<div style={{ width: '40vw', height: '23vw' }}>
  <iframe 
      src="//player.bilibili.com/player.html?isOutside=true&aid=112886840034440&bvid=BV1ykvve9EQA&cid=500001634917907&p=1" 
      scrolling="no" 
      border="0" 
      frameborder="no" 
      framespacing="0" 
      allowfullscreen="true" 
      style={{ width: '100%', height: '100%' }}>
  </iframe>
</div>
*/}
## 拆解过程
### 外壳拆解
四周共四颗T1.5螺丝，两颗位于底部，两颗位于侧面。  
底部也有四颗螺丝 用于固定内部散热结构。

![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/screw-bottom.png)
![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/screw-side.png)

打开上盖时切勿用力过猛，内部有与屏幕连接的FCB排线

![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/open.png)
![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/inter-top.png)


### 电路板模块分离
产品共两块电路板，通过螺丝固定在一块CNC铝散热器上，通过导热凝胶进行热量传递。分离前先断开连接BTB，风扇排线，随后拧下螺丝。

![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/pcb-fan.png)
![abc](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/disassembly/pcb-fpc.png)

