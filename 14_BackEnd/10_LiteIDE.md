### LiteIDE download
From https://github.com/visualfc/liteide/releases .
```bash
wget https://github.com/visualfc/liteide/releases/download/x36.2/liteidex36.1.linux64-qt5.5.1.AppImage
```
* version with qt 5.x.y
* version as AppImage
* view->options->LiteEditor->Fonts&Colors->Sublime

Create desktop shortcut:
```bash
vi ~/Desktop/liteide.desktop
chmod +x ~/Desktop/liteide.desktop
```
With contents:
```bash
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Icon=/home/tudi/Pictures/Oxygen-Icons.org-Oxygen-Categories-applications-system.ico
Exec=/home/tudi/liteidex36.2.linux64-qt5.5.1.AppImage
Name=LiteIDE
GenericName=IDE
```