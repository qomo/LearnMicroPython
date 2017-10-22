# MicroPython On ESP8266  

硬件采用一块ESP8266的nodemcu模组  
![nodemcu模组](./imgs/img_nodemcu_compress.jpg)

## 烧录镜像  

### 下载镜像和工具
- 镜像下载：http://www.micropython.org/download#esp8266  
- 工具安装：'pip install esptool'  
> 这是用来flash firmware到esp8266的工具  

### 刷镜像  
1. 将nodemcu的节点权限设为777  
<pre><code>
LearnMicroPython$ ls -l /dev/ttyUSB0  
crw-rw---- 1 root dialout 188, 0 10月 22 11:54 /dev/ttyUSB0
LearnMicroPython$ sudo chmod 777 /dev/ttyUSB0 
LearnMicroPython$ ls -l /dev/ttyUSB0 
crwxrwxrwx 1 root dialout 188, 0 10月 22 11:54 /dev/ttyUSB0
</code></pre>

2. 按住FLASH按钮，用以下指令擦除flash里的数据  
<pre><code>
$ esptool.py --port /dev/ttyUSB0 erase_flash
esptool.py v1.2
Connecting...
Running Cesanta flasher stub...
Erasing flash (this may take a while)...
Erase took 0.5 seconds
</code></pre>

3. 按住FLASH按钮，用以下指令刷firmware  
<pre><code>
$ esptool.py --port /dev/ttyUSB0 --baud 115200 write_flash --flash_size=32m -fm dio 0x00000 esp8266-20170823-v1.9.2.bin 
esptool.py v1.2
Connecting...
Running Cesanta flasher stub...
Flash params set to 0x0240
Writing 602112 @ 0x0... 602112 (100 %)
Wrote 602112 bytes at 0x0 in 52.2 seconds (92.2 kbit/s)...
Leaving...
</code></pre>

4. 用picocom与nodemcu串口链接，建立链接后按RST按键重启nodemcu就可以看到python终端了  
<pre><code>
$ sudo picocom -b 115200 /dev/ttyUSB0 
</code></pre>
