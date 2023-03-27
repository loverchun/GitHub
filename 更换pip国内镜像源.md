#### 更换pip国内镜像源

$$
Windows
$$

1. 打开`cmd`窗口，输入下列命令，打开设置文件

   ```
   pip config edit --editor notepad
   ```

   如果显示`系统找不到指定的路径`，则继续进行第2步操作。

   - 如果显示`文件不存在`，则直接跳到第**`5`**步。

2. 此时可输入`pip config list -v`，查看配置文件详情，如果不显示内容，则说明尚未配置过。

3. 输入下述命令，目的是在目录中添加配置文件。

   ```
   pip config set x.y z
   ```

4. 输入第一步中的命令打开配置文件。

   ```
   pip config edit --editor notepad
   ```

5. 此时即可添加国内镜像源，我这里采用的是阿里镜像源，因此浏览器打开阿里镜像网站`https://developer.aliyun.com/mirror/`，点击`pypi`，复制其中的***公网配置方法b***到刚才的配置文件中，保存关闭后就大功告成啦，此时就可以畅通无阻地通过pip下载安装各类包了。

$$
Ubuntu(WSL)
$$

1. 打开终端，备份软件源

   ```
   sudo cp -v /etc/apt/sources.list /etc/apt/sources.list_backup
   ```

2. 执行`chmod`命令更改文件权限

   ```
   sudo chmod 777 /etc/apt/sources.list
   ```

3. 选择清华源，打开网址

   `https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/`，复制下述命令完成替换。

   ```
   sudo sed -i "s@http://.*archive.ubuntu.com@https://mirrors.tuna.tsinghua.edu.cn@g" /etc/apt/sources.list
   sudo sed -i "s@http://.*security.ubuntu.com@https://mirrors.tuna.tsinghua.edu.cn@g" /etc/apt/sources.list
   ```

4. 大功告成！

#### 修改pip install默认安装位置

1. 查看`pip`默认安装位置

   1. 点击开始菜单，找到`Anaconda Prompt（Anaconda3），点击进入

      <img src="E:\坚果云-dlut\pictures\image-20230221215141433.png" alt="image-20230221215141433"  />

   2. 在`cmd`中输入

      ```
      python -m site
      ```

      获得

      ![请添加图片描述](E:\坚果云-dlut\pictures\20220720161509112.png)

      其中，

      ```
      D:\\ProgramData\\Anaconda3 ---->是Anaconda安装的位置
      USER_BASE: 'C:\\Users\\kevin\...  ---->表示默认路径在C盘
      USER_SITE: 'C:\\Users\\kevin\...  ---->表示默认路径在C盘
      ```

2. 修改`pip`默认安装位置

      1. `cmd`命令行窗口下键入

         ```
         python -m site -help
         ```

         获得

         ![img](E:\坚果云-dlut\pictures\20220720161509113.png)

      2. 在我的电脑中输入复制的路径

         ![img](E:\坚果云-dlut\pictures\20220720161509115.png)

      3. 打开文件，查找到该位置进行修改

         ![img](E:\坚果云-dlut\pictures\20220720161509116.png)

         ![img](E:\坚果云-dlut\pictures\20220720161509117.png)

      4. 修改路径，并保存（如果提示需要管理员权限，则使用管理员权限运行打开）

         ```
         USER_SITE = "D:\ProgramData\Anaconda3\lib\site-packages"
         USER_BASE = "D:\ProgramData\Anaconda3\Scripts"
         ```

      5. 测试，在`cmd`中输入

         ```
         pip install numpy
         ```

      6. 修改成功！

   

   
