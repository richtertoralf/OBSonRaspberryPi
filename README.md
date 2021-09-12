# OBSonRaspberryPi
Installing OBS Studio on the raspberryPi 4  

It really works. You can install OBS Studio on a RaspberryPi.  

## Raspberry Pi App Store
There are elaborate solutions or very simple ones. Here is the simplest solution:  
First I install the Raspberry Pi App Store.  
` wget -qO- https://raw.githubusercontent.com/Botspot/pi-apps/master/install | bash`  

Now you have lots of additional programs that can be installed on your raspberry Pi with just a mouse click.  

## Install OBS-Studio
You can find the Pi App Store under Accessories. Click on Pi Apps and then on Multimedia. There you will find OBS-Studio. With a mouse click you can now install OBS.  

Don't expect miracles. If you want to work with many sources and many filters, the Raspberry Pi is the wrong hardware.  
Just try it out yourself and see what works.  

I have previously installed ffmepg with SRT and SRT-Live-Transmit. My idea is to use multiple Raspberry Pi to have a pre-produced stream discussed by multiple commentators and thus produce in multiple languages.

## Install ffmpeg with SRT
```
# run as user pi:  
cd ~  
mkdir ~/ffmpegsource  
cd ~/ffmpegsource/    
wget https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-armhf-static.tar.xz  
tar xvf ffmpeg-release-armhf-static.tar.xz  
cd ffmpeg-4.4-armhf-static/  
sudo mv ffmpeg ffprobe /usr/local/bin/
```
## Install srt-live-tranmsit
```
# run as user pi:
sudo apt install tclsh pkg-config cmake libssl-dev build-essential  
mkdir -p ~/ffmpeg_sources ~/bin  
cd ~/ffmpeg_sources  
git clone https://github.com/Haivision/srt.git  
cd srt  
./configure  
make -j$(nproc)  
sudo make install  
sudo cp -v ~/ffmpeg_sources/srt/lib*.* /usr/local/lib/  
sudo ldconfig  
```
