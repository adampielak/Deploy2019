(OS: 8+ Gb RAM)

1. install Android Studio
wget https://dl.google.com/dl/android/studio/ide-zips/3.0.1.0/android-studio-ide-171.4443003-linux.zip
unzip downloaded file

sudo mv android-studio /usr/local

./usr/local/android-studio/studio.sh
custom installation - install virtual device for emulator

create link for x86 computers:
in /Android/Sdl/tools/lib run ln -s emulator emulator-x86

2. install needed lbraries for ubuntu 64b
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386

3. install Flutter repo in Android Studio
4. after Android Studio restart install Flutter SDK


