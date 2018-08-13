# centos7安装oracle11g-client
> 由于oracle11g-client安装包里自带的jdk版本为1.5，可能与本机自带的jdk版本不一致，可能导致安装过程界面出现一些问题，比如中文乱码，对话框显示不出来等。解决办法：

1. 通过locale命令确定下环境变量LANG=zh_CN.UTF-8
2. 找到本机jdk安装路径：which java，通过ls -lrt命令找到软件链接的真实地方。
3. 修改系统环境变量/etc/profile：
> export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.102-4.b14.el7.x86_64
> export JRE_HOME=$JAVA_HOME/jre
> export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
> export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
4. 修改oracle环境变量 vi /home/oracle/.bash_profile
> export ORACLE_BASE=/oracle/app/oracle
> export ORACLE_HOME=$ORACLE_BASE/product/11.2.0/client_1
> export JAVA_BIN=$JAVA_HOME/bin
> export PATH=$ORACLE_HOME/bin:$PATH
> export NLS_LANG="Simplified Chinese_china".ZHS16GBK
5. ./runInstaller -jreLoc $JRE_HOME
