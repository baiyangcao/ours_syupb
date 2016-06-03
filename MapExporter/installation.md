# 安装说明

## 环境要求

- ArcGIS Desktop 10.1
- python 2.7（安装ArcGIS时自带）
- MapExporter安装包，目录结构如下

![MapExporter安装包目录结构](../images/MapExporter_Installation_Folder.png)

## 安装

### 环境变量设置

检查PATH环境变量中是否存在Python路径，**推荐使用32位的Python**，若在安装ArcGIS时没有指定python的安装目录，32位的安装目录应该是**C:\Python27\ArcGIS10.1**，64位python的安装目录为C:\Python27\ArcGISx6410.1，这里使用`C:\Python27\ArcGIS10.1`    

设置完成后打开`cmd`直接数据`python`回车，若设置成功则输出如下，注意位数    

![python环境变量设置](../images/MapExporter_PATH_Python.png)


### Flask及相关组件安装

打开`cmd`窗口，切换到MapExporter所在的文件夹，安装01-06文件内的python包，

 1. 首先切换到MapExporter所在文件夹 `cd [MapExporterFolder]`
 2. 安装`setuptools`：
    - `cd "01 setuptools-21.1.0"`
    - `python setup.py install`
    - `cd ..`
 3. 安装`itsdangerous`:
    - `cd "02 itsdangerous-0.24"`
    - `python setup.py install`
    - `cd ..`
 4. 安装`MarkupSafe`:
    - `cd "03 MarkupSafe-0.23"`
    - `python setup.py install`
    - `cd ..`
 5. 安装`Jinja2`:
    - `cd "04 Jinja2-2.8"`
    - `python setup.py install`
    - `cd ..`
 6. 安装`Werkzeug`:
    - `cd "05 Werkzeug-0.11.3"`
    - `python setup.py install`
    - `cd ..`
 7. 安装`Flask`:
    - `cd "06 Flask-0.10.1"`
    - `python setup.py install`
    - `cd ..`

### 启动MapExporter服务

在`cmd`窗口中，切换到`07 MapExporter`文件夹下，执行`python [MapExporter.py文件的绝对路径]`，得到如下输出

```
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
```
则服务启动成功，打开浏览器地址栏中输入`http://0.0.0.0:5000/`可以看到`Hello World!`，服务运行的`cmd`窗口中可以看到相应的访问日志信息    

### 关闭MapExporter服务

服务运行期间不可以关闭`cmd`窗口，关闭服务在窗口中按下`CTRL+C`即可，或直接关闭`cmd`窗口
 