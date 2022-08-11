[TOC]

# Ubuntu22.04离线安装mysql_8.0.20(同时适用于Ubuntu20.04 LTS)

#### 下载离线包
>https://downloads.mysql.com/archives/community/

![图 1](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E4%B8%8B%E8%BD%BDmysql%E5%AE%89%E8%A3%85%E5%8C%85.png)  

**bu**

**下载完成，如图：**
![图 2](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E4%B8%8B%E8%BD%BD%E7%9A%84mysql%E5%AE%89%E8%A3%85%E5%8C%85.png)  


#### 下载后续需要的依赖文件

**Ubuntu22.04和Ubuntu20.04 LTS 安装mysql的区别就在于这里依赖的文件的版本**

**需要下载的两个文件：**
>libaio1_0.3.112-13build1_amd64.deb
>链接：https://pkgs.org/download/libaio1
>libmecab2_0.996-14build9_amd64.deb
>链接：https://pkgs.org/download/libmecab2

![图 4](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E4%B8%8B%E8%BD%BDlibaio1.png)  

![图 5](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E4%B8%8B%E8%BD%BDlibmecab2.png)  

**下载完成，如图：**
![图 3](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E4%BE%9D%E8%B5%96%E5%8C%85.png)  

#### 安装
1. 将下载好的文件想办法搞到Ubuntu系统中
   ![图 6](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E6%96%87%E4%BB%B6%E6%94%BE%E5%85%A5Ubuntu%E7%B3%BB%E7%BB%9F.png)  

2. 选一个目录，解压`mysql-server_8.0.20-2ubuntu20.04_amd64.deb-bundle.tar`，这里我将文件解压到`/usr/local/mysql/mysql_8.0.20`
    记得给目标文件夹写入的权限，否则会报错
    ![图 7](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E8%A7%A3%E5%8E%8B.png)  

    ![图 8](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E8%A7%A3%E5%8E%8B%E5%90%8E%E5%86%85%E5%AE%B9.png)  

3. 将`libaio1_0.3.112-13build1_amd64.deb`和`libmecab2_0.996-14build9_amd64.deb`也放入到`/usr/local/mysql/mysql_8.0.20`
   现在，目录内容如图：
   ![图 9](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E6%89%80%E6%9C%89%E6%96%87%E4%BB%B6.png)  

4. 依次执行下列命令进行安装，这个过程应该不会出问题
   > sudo dpkg -i mysql-community-client-core_8.0.20-2ubuntu20.04_amd64.deb
   > sudo dpkg -i mysql-common_8.0.20-2ubuntu20.04_amd64.deb
   > sudo dpkg -i mysql-community-client_8.0.20-2ubuntu20.04_amd64.deb
   > sudo dpkg -i libmysqlclient21_8.0.20-2ubuntu20.04_amd64.deb
   > sudo dpkg -i libmysqlclient-dev_8.0.20-2ubuntu20.04_amd64.deb
   > sudo dpkg -i mysql-client_8.0.20-2ubuntu20.04_amd64.deb

   ![图 10](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E6%89%A7%E8%A1%8C%E5%85%AD%E6%9D%A1%E8%AF%AD%E5%8F%A5.png)  

    继续执行下列语句
   >sudo dpkg -i mysql-community-server-core_8.0.20-2ubuntu20.04_amd64.deb

    应该会报错
   ![图 11](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E7%BC%BA%E5%B0%91%E4%BE%9D%E8%B5%96%E5%8C%85.png)  

    不要慌，缺少的包一开始就下好了，直接安装就行
    >sudo dpkg -i libaio1_0.3.112-13build1_amd64.deb
    >sudo dpkg -i libmecab2_0.996-14build9_amd64.deb

    ![图 12](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E8%A7%A3%E5%86%B3%E4%BE%9D%E8%B5%96%E7%BC%BA%E5%A4%B1.png) 

    重新执行`sudo dpkg -i mysql-community-server-core_8.0.20-2ubuntu20.04_amd64.deb`

    ![图 13](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E9%87%8D%E6%96%B0%E6%89%A7%E8%A1%8C.png)  

    接下来继续安装
    执行：`sudo dpkg -i mysql-community-server_8.0.20-2ubuntu20.04_amd64.deb`
    会弹出窗口让你输`密码`，这个`密码`就是`mysql`数据库的`root`账号的`密码`
    ![图 14](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E8%BE%93%E5%85%A5%E5%AF%86%E7%A0%81.png)  

    然后会让你再输一遍，之后跳到下图界面，直接用它推荐的就行
    ![图 15](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E7%94%A8%E6%8E%A8%E8%8D%90%E7%9A%84.png)  

    按完enter后会回到terminal，这里需要在terminal界面等一下，等它安装完。
    ![图 16](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E5%AE%89%E8%A3%85server.png)  

    最后，执行：`sudo dpkg -i mysql-server_8.0.20-2ubuntu20.04_amd64.deb`
    ![图 17](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E5%AE%89%E8%A3%85mysql-server.png)  

    至此，安装完成，mysql已经可以使用了。

5. 执行：`mysql -uroot -p`，然后输入`root`密码，即可登录`mysql`
   ![图 18](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E7%99%BB%E5%BD%95mysql.png)  

    执行`show databases;`查看所有数据库
    ![图 19](https://cdn.jsdelivr.net/gh/PIAOIII/notes_static/imgs/ubuntu22.04%E7%A6%BB%E7%BA%BF%E5%AE%89%E8%A3%85mysql8.0.20(%E5%90%8C%E6%97%B6%E9%80%82%E7%94%A8%E4%BA%8EUbuntu20.04%20LTS)-%E6%9F%A5%E7%9C%8B%E6%89%80%E6%9C%89%E6%95%B0%E6%8D%AE%E5%BA%93.png)  
