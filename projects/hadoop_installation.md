# Hadoop Installation

|Author|Email|Date|
|------|-----|----|
|Van Quoc Mai|maiquocvan@gmail.com|April 10, 2017|

## 1. Install Linux Operation System
Hadoop is supported by GNU/Linux platform and its flavors. Therefore, we have to install a Linux operating system for setting up Hadoop environment.

### 1.1 Download CentOS 7
You could get the CentOS iso file from centos site. In here, I get CentOS-7-x86_64-Minimal-1611.iso

### 1.2 Create CentOS VM
Use VMware Workstation to create a VM to install CentOS7.
You could modify the the resources (RAM, size of VM) as you want. But I think 4G RAM is OK.

### 1.3 Install GNOME
As default, the shell windows will appear after rebooting. You should install GNOME (Graphic User Interface) to use easily.
To setup GUI, you could use the commands:

    #dhclient
    #yum groupinstall "X Window System"
    #yum install gnome-classic-session gnome-terminal nautilus-open-terminal control-center liberation-mono-fonts
    #unlink /etc/systemd/system/default.target
    #ln -sf /lib/systemd/system/graphical.target /etc/systemd/system/default.target
    #reboot

### 1.4 Configuring a DHCP Client

You should do this job to configure the internet connection

    Step 1: The /etc/sysconfig/network file should contain the following line:
        NETWORKING=yes
    Step 2: The /etc/sysconfig/network-scripts/ifcfg-ens33 file should contain the following lines:
        DEVICE=eth0
        BOOTPROTO=dhcp
        ONBOOT=yes

You could check ifcfg-name by ifconfig command.
## 2. Install Hadoop 2.7.3 Single-Node Cluster
Name
	
Version
CentOS	7
Oracle VM Virtualbox	5.0.20
Hadoop	2.7.3
HBase	1.2.4
Hive	2.1.1
Apache Derby	10.8.3.0

 
## 2.1 Install Core Components

You could get more details from https://www.tutorialspoint.com/hadoop/hadoop_enviornment_setup.htm

### 2.1.1 Pre-installation Setup

    Creating a User
        #su
        #adduser hadoop
        #passwd hadoop
    SSH Setup and Key Generation
        #ssh-keygen -t rsa
        #cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
        #chmod 0600 ~/.ssh/authorized_keys
    Reboot and re-login with hadoop user

### 2.1.2 Install Java

    Install Java 1.8.0
        #yum install java-1.8.0-openjdk-devel.x86_64

    Set Java environment variables in ~/bashrc file
        export JAVA_HOME=/etc/alternatives/java_sdk_1.8.0
        export JRE_HOME=$JAVA_HOME/jre
        export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin

### 2.1.3 Install Hadoop (standalone)

    Download Hadoop 2.7.3
        #wget http://apache.claz.org/hadoop/common/hadoop-2.7.3/hadoop-2.7.3.tar.gz
        #mv hadoop-2.7.3.tar.gz /usr/local
        #cd /usr/local
        #tar -xf hadoop-2.7.3.tar.gz
        #move hadoop-2.7.3 hadoop
    Change mode hadoop to 777 to let all users could use
        #sudo chmod 777 -R hadoop
    Set Hadoop environment variables in ~/.bashrc file
        export HADOOP_HOME=/usr/local/hadoop
        export HADOOP_INSTALL=$HADOOP_HOME
        export HADOOP_MAPRED_HOME=$HADOOP_HOME
        export HADOOP_COMMON_HOME=$HADOOP_HOME
        export HADOOP_HDFS_HOME=$HADOOP_HOME
        export YARN_HOME=$HADOOP_HOME
        export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
        export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
    Then apply the changes in current running environment
        #source ~/.bashrc
    Test Hadoop installation by WordCount example
        Create 'input' folder to contain text files
            #cd ~
            #mkdir input
            #cp $HADOOP_HOME/*.txt input
            #ls -l input
        Execute by a JAR example
            #hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.3.jar wordcount input output
        Check the result
            #cat output/*

### 2.1.4 Installing Hadoop in Pseudo Distributed Mode
You could get more details about installing Hadoop in Pseudo Distributed Mode in https://www.tutorialspoint.com/hadoop/hadoop_enviornment_setup.htm

    Configuration Hadoop
        #cd $HADOOP_HOME/etc/hadoop
        Edit hadoop-env.sh
            NOTE: the path of java is /etc/alternatives/java_sdk_1.8.0
        Edit core-site.xml
            NOTE: the value of <name> and <value> elements must not contain ANY space
        Edit hdfs-site.xml
        Edit yarn-site.xml
    Verifying Hadoop Installation
        Name Node Setup
            #cd ~
            #hdfs namenode -format
        Verifying Hadoop dfs
            #start-dfs.sh
        Verifying Yarn Script
            #start-yarn.sh
        Accessing Hadoop on Browser
            http://localhost:50070/
        Verify All Applications for Cluster
            http://localhost:8088/

## 2.2 Install Sub Components
### 2.2.1 HBase
You could get more details from https://www.tutorialspoint.com/hbase/hbase_installation.htm
Notes:

    Hbase 1.2.4 from: http://mirrors.viethosting.com/apache/hbase/stable/hbase-1.2.4-bin.tar.gz
    When updating hbase-site.xml in Pseudo-Distributed mode, you must use port 9000
    You also should set HBase environment variables in ~/.bashrc file
        export HBASE_HOME=/usr/local/hbase
        export PATH=$PATH:$HBASE_HOME/bin
    Should change mode /usr/local/hbase to 777 to let all users could use

### 2.2.2 Hive
You could get more details from https://www.tutorialspoint.com/hive/hive_installation.htm
Notes:

    You should get HIVE from http://mirrors.viethosting.com/apache/hive/hive-2.1.1/
    You could get Apache Derby with:
        #wget http://archive.apache.org/dist/db/derby/db-derby-10.8.3.0/db-derby-10.8.3.0-bin.tar.gz
    When configuring Metastore of Hive, in hive-site.xml, you must set temporary directory by replacing ${system:java.io.tmpdir} by /tmp to avoid error.
    You MUST Initialize to current schema for a new Hive setup with:
        #schematool -dbType derby -initSchema
    Should change mode /usr/local/hive to 777 to let all users could use

## 3. Install Hadoop 2.7.3 Multi-Node Cluster
Node|Hostname|IP Address
----|--------|----------
Master|master|192.168.56.105
Slave|slave1|192.168.56.105

### 3.1 Clone Hadoop Single-node VM as master
    VMware Workstation, free version, has not supported clone function. So if you have installed VM in VMware Workstation tool, you must convert the VM image to use in Oracle VM Virtualbox tool.
    Use Oracle VM Virtualbox to clone CentOS VM as master name

### 3.2 Configuration
    Step 1: Open terminal; add the node details in hosts file
    	>#sudo gedit /etc/hosts
    	>192.168.56.105 master
    	>192.168.56.106 slave1

    Step 2: Edit the hostname

    $sudo gedit /etc/hostname
    master

    Step 3: To update hadoop configuration files, go to /usr/local/hadoop/etc/hadoop folder

    $cd /usr/local/hadoop/etc/hadoop

    Step 4: Edit core-site.xml file

    $sudo gedit core-site.xml
    Replace localhost as master

    Step 5: Edit hdfs-site.xml file

    $sudo gedit hdfs-site.xml
    Replace value 1 as 2 (represents the number of datanodes: master and slave1)

    Step 6: Edit yarn-site.xml file

    $sudo gedit yarn-site.xml
    To be added within <configuration> tag
    <property>
     <name>yarn.resourcemanager.resource-tracker.address</name>
     <value>master:8025</value>
    </property>
    <property>
     <name>yarn.resourcemanager.scheduler.address</name>
     <value>master:8030</value>
    </property>
    <property>
     <name>yarn.resourcemanager.address</name>
     <value>master:8050</value>
    </property>

    Step 7: Create datanodes and give ownership

    $cd ~
    $sudo rm -rf hadoopinfra/*
    $sudo mkdir  hadoopinfra/hdfs/datanode

    Step 8: Reboot master

    Step 9: Clone master as slave1
    Step 11: Upate slave1
        Open terminal; edit the hostname
        $sudo gedit /etc/hostname
        slave1
        Reboot slave1
    Step 12: update master
        Open terminal; add master and slaves details
        $sudo gedit /usr/local/hadoop/etc/hadoop/masters
            master
        $sudo gedit /usr/local/hadoop/etc/hadoop/slaves
            master
            slave1
        Create namenode
        $sudo rm -rf ~/hadoopinfra/hdfs/namenode
        $sudo mkdir -p ~/hadoopinfra/hdfs/namenode
        Format the namenode
        $hadoop namenode –format
        The exit status should be 0.
        Start the hadoop daemons
        $start-dfs.sh
        $start-yarn.sh
    Step 13: To see the daemons that are running
    $jps
    In master, it should display SecondaryNamenode, Namenode, ResourceManager and jps
    In slave1, it should display Datanode, NodeManager and jps
    Step 14: To view the hadoop details in browser
    http://master:50070/
    http://master:8088/

### 3.3 Adding new nodes to an existing cluster
    **How to?**
        Step 1: From the master node, update the slaves configuration file with the hostname of the new node:
            #vi /usr/local/hadoop/etc/hadoop/slaves
            master
            slave1
            slave2
        Step 2: Update slave2 in /etc/hosts file. Such as:
            192.168.56.107    slave2
        Step 3: Log in to the new node (slave2) and start the DataNode and TaskTracker services:
            #ssh slave2
            #cd /usr/local/hadoop
            #sbin/hadoop-daemon.sh start datanode
            #sbin/hadoop-daemon.sh start tasktracker
    **How it works?**
        We updated the slaves configuration file on the head node to tell the Hadoop framework that a new node exists in the cluster. However, this file is only read when the Hadoop services are started (for example, by executing the bin/start-all.sh script). In order to add the new node to the cluster without having to restart all of the Hadoop services, we logged into the new node, and started the DataNode and TaskTracker services manually.
    **Note:**
        The DataNode and TaskTracker services will automatically start the next time the cluster is restarted.
    **More**
        When you add a new node to the cluster, the cluster is not properly balanced. HDFS will not automatically redistribute any existing data to the new node in order to balance the cluster. To rebalance the existing data in the cluster, you can run the following command from the head node:
        #sbin/start-balancer.sh

### 3.4 Safely decommissioning nodes
