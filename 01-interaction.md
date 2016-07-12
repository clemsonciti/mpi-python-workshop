---
layout: lesson
title: Introduction to Hadoop
subtitle: Interacting with Hadoop
minutes: 20
---

> ## Learning objectives {.objectives}
> * Learn how to access the web-based Jupyter notebook.
> * Learn how to use the Hadoop command in Jupyter shells.
> * Learn how to access the web UI of the Hadoop Distributed File System.

In this workshop, we will leverage the Jupyter infrastructure at Clemson
University to directly interact with Hadoop.

## Jupyter

To start using the Jupyter notebook, go to **https://webapp01-ext.palmetto.clemson.edu:8443**
and sign in with your Clemson credentials. Next, click **Start My Server** to
spawn a new Jupyter notebook. You should see the content of your home directory
 on Palmetto under **Files**.
<br>
<img src="fig/jupyter/login.png" \
     alt="Login" \
     style="height:300px">
<br>
Under **New**, create a new folder. This folder will appear immediately in your
 home directly with the name **Untitled Folder**. Check the selection box next
 to this folder, a button called **Rename** will appear below the **Files**
 tab. Click this button to change this folder to a name of your choice. Click
 on this folder to go to the next level.
<br>
<img src="fig/jupyter/folder.png" \
     alt="Create New Folder" \
     style="height:300px">
<br>
Use the menu under **New** once again to create a new Jupyter notebook using
Python 3.0 distributed through Anaconda 2.5.0 by Continuum.
<br>
<img src="fig/jupyter/notebook.png" \
     alt="Create New Folder" \
     style="height:300px">
<br>
Change the name of this notebook to "Introduction to Hadoop".
<br>
<img src="fig/jupyter/notebook-2.png" \
     alt="Create New Folder" \
     style="height:300px">
<br>
For this workshop, the default codes inside a cell will be interpreted as Python
 language. However, any line that begins with **!** will be interpreted as a
 Linux system command.
<br>

~~~{.bash}
print "Hello World"
~~~

~~~ {.output}
Hello World
~~~

~~~{.bash}
!ls -l /
~~~

~~~ {.output}
total 424
dr-xr-xr-x.    2 root   root     4096 Feb 26 04:18 bin
drwxrws---    30 root   bioengr  4096 Apr 18 18:31 bioengr
dr-xr-xr-x.    4 root   root     4096 Jan 26 17:22 boot
drwxr-xr-x.   10 root   root     4096 Oct 17  2014 cgroup
drwxr-xr-x     3 root   root     4096 Aug  4  2015 cgroups_test
drwxr-xr-x    24 root   root     4096 Apr 27 16:54 common
lrwxrwxrwx.    1 root   root        7 Oct 17  2014 common1 -> /common
drwxrwxr-x    17 root   cugi     4096 Mar  4 16:27 cugi
drwxr-xr-x    18 root   root     4240 Feb 26 14:09 dev
drwxr-xr-x.  148 root   root    12288 May 10 14:49 etc
drwxr-xr-x.    2 root   root     4096 Oct 17  2014 fast
drwxrws---    24 root   feltus   4096 Apr  8 11:17 feltus
drwxr-xr-x     3 root   root     4096 Apr 26  2015 hadoop
drwxr-xr-x    17 root   root     4096 Dec  2 11:31 hdp_service_accounts
drwxr-xr-x  1845 root   root    77824 May 10 14:47 home
dr-xr-xr-x.   13 root   root     4096 Feb 26 04:18 lib
dr-xr-xr-x.   10 root   root    12288 Feb 26 04:18 lib64
drwxr-xr-x.    4 root   root     4096 Apr 26  2015 local
drwx------.    2 root   root    16384 Oct 17  2014 lost+found
drwxr-xr-x.    2 root   root     4096 Jan 28 17:10 media
drwxr-xr-x     8 root   root     4096 May 16  2014 misc
drwxr-xr-x.    2 root   root     4096 Jul 20  2011 mnt
drwxr-xr-x     3 nagios nagios   4096 Oct 10  2014 nagios
drwxr-xr-x.    2 root   root     4096 Sep 25  2013 net
drwxr-xr-x     9 root   root     4096 Nov  3  2014 nsr
drwxrwxr-x.   56 root   root     4096 Mar  9 19:36 opt
drwxrws---    23 root   panicle  4096 Feb 11 13:15 panicle
dr-xr-xr-x   481 root   root        0 Feb 26 14:08 proc
dr-xr-x---.   15 root   root     4096 May 10 15:00 root
dr-xr-xr-x.    2 root   root    12288 Feb 26 04:18 sbin
drwxr-xr-x     2 root   root     4096 Sep  2  2015 scratch1
drwxr-xr-x  1740 root   root     1740 May 10 14:47 scratch2
drwxr-xr-x.    2 root   root     4096 Oct 17  2014 selinux
drwxrws---    14 root   smlc     4096 Apr 18 13:21 smlc
drwxr-xr-x   117 root   root     4096 Apr 13 14:42 software
drwxr-xr-x.    2 root   root     4096 Jul 20  2011 srv
drwxr-xr-x    13 root   root        0 Feb 26 14:08 sys
drwxrwxrwt.  574 hbase  hadoop  45056 May 10 06:06 tmp
drwxr-xr-x.   18 root   root     4096 Feb  5  2015 usr
drwxr-xr-x.   23 root   root     4096 Oct 17  2014 var
drwx------.    9 root   root     4096 Oct 17  2014 xcatpost
~~~

## HDFS commands
HDFS provides a set of commands for users to interact with the system from a
 Linux-based terminal. To view all available HDFS systems commands, run the
 following in a cell:

~~~{.bash}
!ssh dsciu001 hdfs
~~~

~~~ {.output}
Usage: hdfs [--config confdir] [--loglevel loglevel] COMMAND
       where COMMAND is one of:
  dfs                  run a filesystem command on the file systems supported in Hadoop.
  classpath            prints the classpath
  namenode -format     format the DFS filesystem
  secondarynamenode    run the DFS secondary namenode
  namenode             run the DFS namenode
  journalnode          run the DFS journalnode
  zkfc                 run the ZK Failover Controller daemon
  datanode             run a DFS datanode
  dfsadmin             run a DFS admin client
  haadmin              run a DFS HA admin client
  fsck                 run a DFS filesystem checking utility
  balancer             run a cluster balancing utility
  jmxget               get JMX exported values from NameNode or DataNode.
  mover                run a utility to move block replicas across
                       storage types
  oiv                  apply the offline fsimage viewer to an fsimage
  oiv_legacy           apply the offline fsimage viewer to an legacy fsimage
  oev                  apply the offline edits viewer to an edits file
  fetchdt              fetch a delegation token from the NameNode
  getconf              get config values from configuration
  groups               get the groups which users belong to
  snapshotDiff         diff two snapshots of a directory or diff the
                       current directory contents with a snapshot
  lsSnapshottableDir   list all snapshottable dirs owned by the current user
						Use -help to see options
  portmap              run a portmap service
  nfs3                 run an NFS version 3 gateway
  cacheadmin           configure the HDFS cache
  crypto               configure HDFS encryption zones
  storagepolicies      list/get/set block storage policies
  version              print the version

Most commands print help when invoked w/o parameters.
~~~

For this workshop, we are interested in file system commands. Create a new cell
 and run the following:

~~~{.bash}
!ssh dsciu001 hdfs dfs
~~~

~~~ {.output}
Usage: hadoop fs [generic options]
	[-appendToFile <localsrc> ... <dst>]
	[-cat [-ignoreCrc] <src> ...]
	[-checksum <src> ...]
	[-chgrp [-R] GROUP PATH...]
	[-chmod [-R] <MODE[,MODE]... | OCTALMODE> PATH...]
	[-chown [-R] [OWNER][:[GROUP]] PATH...]
	[-copyFromLocal [-f] [-p] [-l] <localsrc> ... <dst>]
	[-copyToLocal [-p] [-ignoreCrc] [-crc] <src> ... <localdst>]
	[-count [-q] [-h] [-v] [-t [<storage type>]] <path> ...]
	[-cp [-f] [-p | -p[topax]] <src> ... <dst>]
	[-createSnapshot <snapshotDir> [<snapshotName>]]
	[-deleteSnapshot <snapshotDir> <snapshotName>]
	[-df [-h] [<path> ...]]
	[-du [-s] [-h] <path> ...]
	[-expunge]
	[-find <path> ... <expression> ...]
	[-get [-p] [-ignoreCrc] [-crc] <src> ... <localdst>]
	[-getfacl [-R] <path>]
	[-getfattr [-R] {-n name | -d} [-e en] <path>]
	[-getmerge [-nl] <src> <localdst>]
	[-help [cmd ...]]
	[-ls [-d] [-h] [-R] [<path> ...]]
	[-mkdir [-p] <path> ...]
	[-moveFromLocal <localsrc> ... <dst>]
	[-moveToLocal <src> <localdst>]
	[-mv <src> ... <dst>]
	[-put [-f] [-p] [-l] <localsrc> ... <dst>]
	[-renameSnapshot <snapshotDir> <oldName> <newName>]
	[-rm [-f] [-r|-R] [-skipTrash] [-safely] <src> ...]
	[-rmdir [--ignore-fail-on-non-empty] <dir> ...]
	[-setfacl [-R] [{-b|-k} {-m|-x <acl_spec>} <path>]|[--set <acl_spec> <path>]]
	[-setfattr {-n name [-v value] | -x name} <path>]
	[-setrep [-R] [-w] <rep> <path> ...]
	[-stat [format] <path> ...]
	[-tail [-f] <file>]
	[-test -[defsz] <path>]
	[-text [-ignoreCrc] <src> ...]
	[-touchz <path> ...]
	[-truncate [-w] <length> <path> ...]
	[-usage [cmd ...]]

Generic options supported are
-conf <configuration file>     specify an application configuration file
-D <property=value>            use value for given property
-fs <local|namenode:port>      specify a namenode
-jt <local|resourcemanager:port>    specify a ResourceManager
-files <comma separated list of files>    specify comma separated files to be copied to the map reduce cluster
-libjars <comma separated list of jars>    specify comma separated jar files to include in the classpath.
-archives <comma separated list of archives>    specify comma separated archives to be unarchived on the compute machines.

The general command line syntax is
bin/hadoop command [genericOptions] [commandOptions]
~~~

We can see that HDFS provides a number of file system commands that are quite
similar to their Linux counterpart. For example, ***-chown*** and ***-chmod***
 change ownership and permission of HDFS files and directories, ***-ls*** lists
  content of a directory, ***-mkdir*** creates new directory, ***-rm*** removes
   files and directories, and so on.

> ## ***hadoop fs*** and ***hdfs dfs*** {.callout}
>
> ***hadoop fs*** is an older syntax for ***hdfs dfs***. While both commands
> produce the same results, you are encouraged to use ***hdfs dfs*** instead.

When a Hadoop cluster is first started, there is no data. Users usually import
 data into the cluster from the traditional Linux-based file system. This is
 done by using the commandOption ***-put***. Vice versa, to move data from HDFS
 back to a Linux-based file system, commandOption ***-get*** is used.

> ## Hadoop Distributed File System is not the Linux File System {.callout}
>
> It is important to distinguish between the files and directories that are
> stored on HDFS and those that are stored on the Linux File Systems. In the
> Hadoop usage guide, the prefix ***local*** implies a path to a file/directory
> that is on a Linux File System. Anything else implies a path to a
> file/directory on HDFS

## HDFS Web Interface
At Clemson University, the Hadoop Big Data infrastructure is called the Cypress
cluster. It uses an open source flavor of Hadoop distributed by Hortonworks.
HDFS provides a web-based user interface for users to view stored data. The
interface is hosted on HDFS' NameNode, which is replicated to ensure
uninterrupted operation. The URLs of the NameNode replicates are:
<br>
~~~ {.output}
http://namenode1.palmetto.clemson.edu:50070
http://namenode2.palmetto.clemson.edu:50070
~~~
<br>
<img src="fig/Namenodes.png" \
     alt="Namnodes" \
     style="height:500px">
<br>
This figure shows the interfaces of the two HDFS NameNode replications.
Only the active instance (left) can be used to view files and directories.

## Check your understanding: Using Jupyter shell to download data {.callout}

Create a directory named **intro-to-hadoop** in your home directory on Palmetto

From inside this directory, run the following command to get data from github

~~~{.bash}
!git clone https://github.com/clemsoncoe/Introduction-to-Hadoop-data.git
~~~

View this newly cloned directory to confirm that you have the file ***gutenberg-shakespeare.txt***.

## Check your understanding: View files and directories on HDFS {.challenge}

View the content of your HDFS user directory (/user/**your-username**) on
 Cypress

## Check your understanding: Create directory on HDFS {.challenge}

Create a directory in your HDFS user directory named **intro-to-hadoop**

## Check your understanding: Import file to HDFS {.challenge}

Copy the file ***gutenberg-shakespeare.txt*** from Palmetto to this newly
 created **intro-to-hadoop** directory on HDFS using **put**. View the content of
 the **intro-to-hadoop** directory to confirm that the file has been
 successfully uploaded.
