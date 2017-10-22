# MicroPython On ESP8266  

硬件采用一块ESP8266的nodemcu模组  
![nodemcu模组](./imgs/img_nodemcu_compress.jpg)

## 烧录镜像  

### 下载镜像和工具
- 镜像下载：http://www.micropython.org/download#esp8266  
- 工具安装：'''pip install esptool'''  
> 这是用来flash firmware到esp8266的工具  

### 刷镜像  
1. 将nodemcu的节点权限设为777  
<pre><code>
LearnMicroPython$ ls -l /dev/ttyUSB0  
crw-rw---- 1 root dialout 188, 0 10月 22 11:54 /dev/ttyUSB0
LearnMicroPython$ sudo chmod 777 /dev/ttyUSB0 
LearnMicroPython$ ls -l /dev/ttyUSB0 crwxrwxrwx 1 root dialout 188, 0 10月 22 11:54 /dev/ttyUSB0
</code></pre>
