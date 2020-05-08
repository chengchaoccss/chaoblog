```python
QtCore.QCoreApplication.setAttribute(QtCore.Qt.AA_EnableHighDpiScaling) #解决了Qtdesigner设计的界面与实际运行界面不一致的问题
app = QApplication(sys.argv)
mainwin = QMainWindow()
ui = buddy.Ui_MainWindow()   
ui.setupUi(mainwin)
ui.pushButton.clicked.connect(nameclick)
ui.pushButton_2.clicked.connect(closeclick)
mainwin.show()
sys.exit(app.exec_())
```