# docker_mongod
root@Hackgeek-Srv:/mongo-docker# docker build -t mongod-replica/mongodb .
Sending build context to Docker daemon  2.048kB
Step 1/6 : FROM centos:centos7
centos7: Pulling from library/centos
d9aaf4d82f24: Pull complete 
Digest: sha256:eba772bac22c86d7d6e72421b4700c3f894ab6e35475a34014ff8de74c10872e
Status: Downloaded newer image for centos:centos7
 ---> 196e0ce0c9fb
Step 2/6 : MAINTAINER The CentOS Project <cloud-ops@centos.org>
 ---> Running in 8644d0ac1ddd
 ---> 786e2ae361ed
Removing intermediate container 8644d0ac1ddd
Step 3/6 : RUN yum -y update;yum clean all
 ---> Running in 09a6d7bb9551
Loaded plugins: fastestmirror, ovl
Determining fastest mirrors
 * base: mirror.solarvps.com
 * extras: mirror.es.its.nyu.edu
 * updates: centos.mirror.constant.com
No packages marked for update
Loaded plugins: fastestmirror, ovl
Cleaning repos: base extras updates
Cleaning up everything
Maybe you want: rm -rf /var/cache/yum, to also free up space taken by orphaned data from disabled or removed repos
Cleaning up list of fastest mirrors
 ---> 852f8780290a
Removing intermediate container 09a6d7bb9551
Step 4/6 : RUN yum -y install epel-release
 ---> Running in c605dbb596e6
Loaded plugins: fastestmirror, ovl
Determining fastest mirrors
 * base: mirror.solarvps.com
 * extras: mirror.es.its.nyu.edu
 * updates: centos.mirror.constant.com
Resolving Dependencies
--> Running transaction check
---> Package epel-release.noarch 0:7-9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                Arch             Version         Repository        Size
================================================================================
Installing:
 epel-release           noarch           7-9             extras            14 k

Transaction Summary
================================================================================
Install  1 Package

Total download size: 14 k
Installed size: 24 k
Downloading packages:
warning: Public key for epel-release-7-9.noarch.rpm is not installed
/var/cache/yum/x86_64/7/extras/packages/epel-release-7-9.noarch.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-4.1708.el7.centos.x86_64 (@CentOS)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : epel-release-7-9.noarch                                      1/1 
  Verifying  : epel-release-7-9.noarch                                      1/1 

Installed:
  epel-release.noarch 0:7-9                                                     

Complete!
 ---> b98c6cb4936a
Removing intermediate container c605dbb596e6
Step 5/6 : RUN yum -y install mongodb-server
 ---> Running in aaec60c50d5b
Loaded plugins: fastestmirror, ovl
Loading mirror speeds from cached hostfile
 * base: mirror.solarvps.com
 * epel: mirror.cs.princeton.edu
 * extras: mirror.es.its.nyu.edu
 * updates: centos.mirror.constant.com
Resolving Dependencies
--> Running transaction check
---> Package mongodb-server.x86_64 0:2.6.12-4.el7 will be installed
--> Processing Dependency: v8 for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libyaml-cpp.so.0.5()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libv8.so.3()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libtcmalloc.so.4()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libstemmer.so.0()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libsnappy.so.1()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libboost_thread-mt.so.1.53.0()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libboost_system-mt.so.1.53.0()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libboost_program_options-mt.so.1.53.0()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Processing Dependency: libboost_filesystem-mt.so.1.53.0()(64bit) for package: mongodb-server-2.6.12-4.el7.x86_64
--> Running transaction check
---> Package boost-filesystem.x86_64 0:1.53.0-27.el7 will be installed
---> Package boost-program-options.x86_64 0:1.53.0-27.el7 will be installed
---> Package boost-system.x86_64 0:1.53.0-27.el7 will be installed
---> Package boost-thread.x86_64 0:1.53.0-27.el7 will be installed
---> Package gperftools-libs.x86_64 0:2.4-8.el7 will be installed
--> Processing Dependency: libunwind.so.8()(64bit) for package: gperftools-libs-2.4-8.el7.x86_64
---> Package libstemmer.x86_64 0:0-2.585svn.el7 will be installed
---> Package snappy.x86_64 0:1.1.0-3.el7 will be installed
---> Package v8.x86_64 1:3.14.5.10-25.el7 will be installed
---> Package yaml-cpp.x86_64 0:0.5.1-6.el7 will be installed
--> Running transaction check
---> Package libunwind.x86_64 2:1.2-2.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                    Arch        Version                 Repository
                                                                           Size
================================================================================
Installing:
 mongodb-server             x86_64      2.6.12-4.el7            epel      6.6 M
Installing for dependencies:
 boost-filesystem           x86_64      1.53.0-27.el7           base       68 k
 boost-program-options      x86_64      1.53.0-27.el7           base      156 k
 boost-system               x86_64      1.53.0-27.el7           base       40 k
 boost-thread               x86_64      1.53.0-27.el7           base       57 k
 gperftools-libs            x86_64      2.4-8.el7               base      272 k
 libstemmer                 x86_64      0-2.585svn.el7          epel       67 k
 libunwind                  x86_64      2:1.2-2.el7             base       57 k
 snappy                     x86_64      1.1.0-3.el7             base       40 k
 v8                         x86_64      1:3.14.5.10-25.el7      epel      3.0 M
 yaml-cpp                   x86_64      0.5.1-6.el7             epel      176 k

Transaction Summary
================================================================================
Install  1 Package (+10 Dependent packages)

Total download size: 11 M
Installed size: 34 M
Downloading packages:
Public key for libstemmer-0-2.585svn.el7.x86_64.rpm is not installed
warning: /var/cache/yum/x86_64/7/epel/packages/libstemmer-0-2.585svn.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 352c64e5: NOKEY
--------------------------------------------------------------------------------
Total                                              448 kB/s |  11 MB  00:24     
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Importing GPG key 0x352C64E5:
 Userid     : "Fedora EPEL (7) <epel@fedoraproject.org>"
 Fingerprint: 91e9 7d7c 4a5e 96f1 7f3e 888f 6a2f aea2 352c 64e5
 Package    : epel-release-7-9.noarch (@extras)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : boost-system-1.53.0-27.el7.x86_64                           1/11 
  Installing : boost-thread-1.53.0-27.el7.x86_64                           2/11 
  Installing : boost-filesystem-1.53.0-27.el7.x86_64                       3/11 
  Installing : yaml-cpp-0.5.1-6.el7.x86_64                                 4/11 
  Installing : boost-program-options-1.53.0-27.el7.x86_64                  5/11 
  Installing : libstemmer-0-2.585svn.el7.x86_64                            6/11 
  Installing : 2:libunwind-1.2-2.el7.x86_64                                7/11 
  Installing : gperftools-libs-2.4-8.el7.x86_64                            8/11 
  Installing : 1:v8-3.14.5.10-25.el7.x86_64                                9/11 
  Installing : snappy-1.1.0-3.el7.x86_64                                  10/11 
  Installing : mongodb-server-2.6.12-4.el7.x86_64                         11/11 
  Verifying  : boost-system-1.53.0-27.el7.x86_64                           1/11 
  Verifying  : snappy-1.1.0-3.el7.x86_64                                   2/11 
  Verifying  : gperftools-libs-2.4-8.el7.x86_64                            3/11 
  Verifying  : 1:v8-3.14.5.10-25.el7.x86_64                                4/11 
  Verifying  : 2:libunwind-1.2-2.el7.x86_64                                5/11 
  Verifying  : boost-thread-1.53.0-27.el7.x86_64                           6/11 
  Verifying  : libstemmer-0-2.585svn.el7.x86_64                            7/11 
  Verifying  : boost-program-options-1.53.0-27.el7.x86_64                  8/11 
  Verifying  : yaml-cpp-0.5.1-6.el7.x86_64                                 9/11 
  Verifying  : mongodb-server-2.6.12-4.el7.x86_64                         10/11 
  Verifying  : boost-filesystem-1.53.0-27.el7.x86_64                      11/11 

Installed:
  mongodb-server.x86_64 0:2.6.12-4.el7                                          

Dependency Installed:
  boost-filesystem.x86_64 0:1.53.0-27.el7                                       
  boost-program-options.x86_64 0:1.53.0-27.el7                                  
  boost-system.x86_64 0:1.53.0-27.el7                                           
  boost-thread.x86_64 0:1.53.0-27.el7                                           
  gperftools-libs.x86_64 0:2.4-8.el7                                            
  libstemmer.x86_64 0:0-2.585svn.el7                                            
  libunwind.x86_64 2:1.2-2.el7                                                  
  snappy.x86_64 0:1.1.0-3.el7                                                   
  v8.x86_64 1:3.14.5.10-25.el7                                                  
  yaml-cpp.x86_64 0:0.5.1-6.el7                                                 

Complete!
 ---> 21cb9fd757b4
Removing intermediate container aaec60c50d5b
Step 6/6 : RUN mkdir -p /data/db
 ---> Running in aadacdc16414
 ---> 6a92df2d43d5
Removing intermediate container aadacdc16414
Successfully built 6a92df2d43d5
Successfully tagged mongod-replica/mongodb:latest
