```python
import sys
from PyQt5.QtWidgets import QWidget
# out = sys.stdout
sys.stdout = open('Qwidget.txt','w')
help(QWidget)
print('这些文字会被存到本地文件中！')
sys.stdout.close()
# sys.stdout = out
```