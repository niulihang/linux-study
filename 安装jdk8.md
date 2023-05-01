# Debian安装Oracle JDK8

1. Oracle官网下载jdk8的tar包（命令行模式jdk8已无法安装）
2. 解压tar包至/usr/lib/java路径，`tar -zxvf ~/jdk-8u202-linux-x64.tar.gz -C /usr/lib/java`
3. 添加环境变量，`vim ~/.bashrc`，

    ```shell
    export JAVA_HOME=/usr/lib/java/jdk1.8.0_202
    export JRE_HOME=${JAVA_HOME}/jre
    export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
    export PATH=${JAVA_HOME}/bin:${PATH}
    ```

4. 刷新环境变量，`source ~/.bashrc`
5. 添加java，`sudo update-alternatives --install /usr/bin/java java /usr/lib/java/jdk1.8.0_202/bin/java 300`，其中，300是优先级
6. 多java环境改变版本，`sudo update-alternatives --config java`
