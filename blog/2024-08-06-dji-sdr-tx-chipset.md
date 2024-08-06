---
slug: teardown/dji-sdr-tx-chipset
title: DJI SDR Transmission TX Chipset Explain
authors: [kelvin,treee]
tags: [DJI]
---
## PCB整体布局
DJI SDR图传发射端电气部分共两块PCBA，一块主要负责射频收发
![DJI SDR transmission,P1 chip,Gegadevice ram](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/pcb/rf-top-resize.webp)
![DJI SDR transmission,Sandisk NAND,IE1000](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/pcb/rf-back-resize.webp)

另一块PCBA则负责io接口编解码部分

![DJI SDR transmission,SDI port,HDMI port,Xilinx fpga Artix 7,Lattice](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/pcb/io-top-resize.webp)
![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/pcb/io-back-resize.webp)


## 方案解析
### RF Module正面
DJI SDR图传中仍然使用了与Mavic3，Avata，图传同款的P1芯片，外挂两颗[Gegadevice GDQ2BFAA](https://www.semiee.com/file2/2a39a95874cb608b11e401de1671fbce/Gigadevice/Gigadevice-DS-00808-XDQ2BFAA-Rev1.4.pdf)的4Gbit的DDR4 SRAM

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/p1-specific-resize.webp)

Wi-Fi芯片[SYN4375](https://cdn.bfldr.com/ZU41R0OK/at/3hww6tbg9cwkz6hkckn5b6m/syn4375-dual-band-wi-fi-bluetooth-rsdb.pdf)也与Mavic3 Pro子板上的芯片为同一型号

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/wifi-specific-resize.webp)

### RF Module反面
反面可见采用两颗IE1000方案,该芯片具体用途猜测是射频前端收发器。  
IE1000与两颗RR77232，两颗RR77235共同构成了射频前端方案，IE1000芯片周围见多颗[RF5602](https://www.qorvo.com/products/d/da000502)，为2.4GHz Linear Power Amplifier

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/ie1000-specific-resize.webp)

### IO Module正面
接口板正面首先映入眼帘的是一颗[Xilinx Artix-7 FPGA](https://www.lcsc.com/datasheet/lcsc_datasheet_2304140030_AMD-XILINX-XC7A50T-1FG484I_C1552448.pdf)，猜测可能作为视频编解码使用

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/xilinx-artix7-codeshot-crop-watermark.jpg)

临近HDMI接口有一颗[Lattice SiI9293](https://www.lcsc.com/datasheet/lcsc_datasheet_1912111437_Lattice-SII9293CNUC_C369568.pdf)的HDMI1.4接收芯片，支持1080p60。  

<a href="https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/lattice-sii9293-codeshot-watermark.jpg" target="original">
  <button>View Original Photo</button>
</a>

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/lattice-sii9293-codeshot-resize.webp)


旁边还有一颗GD32F3单片机，临近系统电源开关开关，猜测可能用于处理电源时序。  
3.5mm耳机接口旁有一颗[NAU88L21](https://www.lcsc.com/datasheet/lcsc_datasheet_2204271615_Nuvoton-Tech-NAU88L21YG_C2917201.pdf)，内置ADC和DAC，用于队内通话音频

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/gd32-audio-crop-watermark.jpg)

### IO Module 背面
SDI接口采用[TI LMH0344](https://www.ti.com/lit/ds/symlink/lmh0344.pdf)方案，最高支持到2.97Gbps数据传输速率

![](https://s3.amazonaws.com/uhenry.wiki/dji-sdr-teardown/ic/sdi-lmh0344-crop-specific-watermark.jpg)

