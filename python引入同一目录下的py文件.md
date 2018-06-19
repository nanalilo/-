# -python引入同一目录下的py文件
python引入同一目录下的py文件

注意：python2和python3的包内import语法有区别，以下为python3的包内import语法

 

例如:在select_data.py文件中要引入db.py文件

1、首先在目录下要有__init__.py文件

2、在select_data.py文件中加入：
  from . import db
  或者
  import .db

（如果要引入同一目录下的db.py文件中的一个类Test，在select_data.py文件中加一行：from .db import Test）

 

可以直接在__init__.py中import，在该目录下的文件都可以使用__init__.py文件中import的东西
