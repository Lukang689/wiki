##### 环境安装

```
pip3 install PyQt5-tools
```

##### PyQt5使用快捷键

```
self.printShortCut = QShortcut(QKeySequence(Qt.Key_9), self)
self.printShortCut.activated.connect(self.onPrinterClicked)
```

##### 捕捉主窗口退出事件

重写closeEvent方法

```
def closeEvent(self, event):
    pass
```

##### 确定取消选择框

```
reply = QMessageBox.question(self, 'title', 'message', QMessageBox.Yes | QMessageBox.No, QMessageBox.No)
if reply == QMessageBox.No:
    print('user select no')

else:
    print('user select yes')
```



