

 

# Miscellaneous

## Stego

1.   常见文件头
[Ref](https://www.garykessler.net/library/file_sigs.html)

### Image
1. Exif信息隐藏
``` bash
exiftool -a -u -g1 hide.jpg
# 查看所有元信息，包括重复和未知标签，并按小组排列
exiftool -gps:all="" hide.jpg
# 清空gps信息
exiftool -all="" hide.jpg
# 清除所有信息
```
[Ref](https://blog.csdn.net/weixin_34393428/article/details/88679127)
2. 宽高
3. 盲水印
+ 若加密数据是**图片**则需要**原始图像**和**加水印图像**
+ 若加密数据是**文本**则仅需要**加水印图像**
[提取图像不再需要原图的工具BlindWaterMark](https://github.com/ww23/BlindWatermark)
4. 与或非运算
+ [StegSolve](StegSolve-1.4.jar) 
#### JPG
+ [steghide](http://steghide.sourceforge.net/download.php)
> 对jpg或wav添加隐藏信息或提取信息
``` bash
steghide embed -cf hide.jpg/vedio.wav -ef hidenmessage.txt
#向图像或视频隐藏信息
steghide info hide.jpg
# 查看图片中嵌入的文件信息
steghide extract -sf hide.jpg
# 提取文件中的隐藏信息
```
+ [stegdetect](stegdetect0.4.zip) 
> 通过统计分析技术评估 JPEG 文件的 DCT 频率系数的隐写工具, 可以检测到通过 JSteg、JPHide、OutGuess、Invisible Secrets、F5、appendX 和 Camouflage 等这些隐写工具隐藏的信息，并且还具有基于字典暴力破解密码方法提取通过 Jphide、outguess 和 jsteg-shell 方式嵌入的隐藏信息。
``` bash
stegdetect -s 10.0 hide.jpg
# s选项指定检测算法的敏感程度，越大则越敏感
```
> 爆破一些需要密码的加密
```bash
stegbreak -r rule.ini -f password.txt -c hide.jpg
```
+ [jphide/jpseek](jphide.zip) 
+ [SilentEye](silenteye-0.4.1.zip) 

>   SilentEye is a cross-platform application design for an easy use of steganography, in this case hiding messages into **pictures(bmp/jpg) or sounds(wav)**. It provides a pretty nice interface and an easy integration of new steganography algorithm and cryptography process by using a plug-ins system.

+ [F5](https://github.com/matthewgao/F5-steganography)
> This package is meant to demonstrate a new steganographic algorithm. It is a very preliminary version to embed files into true colour **BMP, GIF, or JPEG** images. To have secure steganography choose a good passphrase. It is also recommended to scan a new carrier image in true colour BMP format for every new steganographic message. Delete the carrier BMP after you created the lossy compressed steganogram.
#### GIF

+   逐帧提取空间轴信息
``` bash
convert Hide.gif Hide.png
```
+   每一帧间隔时间轴信息
``` bash
identify -format "%s %T \n" Hide.gif
```
+ F5
#### PNG
+ LSB
[StegSolve-1.4.jar](StegSolve-1.4.jar) 