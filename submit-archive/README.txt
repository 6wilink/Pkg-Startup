Submit Package in Archive
-------------------------
by Qige @ 2017.03.14

MD5SUM tells us you got the right archive file.

Let's say:
- package is "app-sample";
- version "1.0", release "1";
- openwrt cc root is "/openwrt";
- current dir is "6w-pkg-startup.git" root;
- brand new package, start with "6w-pkg-startup.git".

STEP I
------
Add/Update your "README.txt" or "CHANGELOG.txt";

STEP II
-------
Pair Makefile & archive file:
a1. Source code directory naming format is "$(PKG_NAME)_$(PKG_VERSION)-$(PKG_RELEASE)", so "app-sample_1.0-1";
a2. Archive must be compressed with format in step a1: "tar cfj app-sample_1.0-1.tar.bz2 app-sample_1.0-1/";
a3.1 Upload "app-sample_1.0-1.tar.bz2" to http/ftp service;
a3.2 "md5sum app-sample_1.0-1.tar.bz2" in Ubuntu; "md5 app-sample_1.0-1.tar.bz2" in Mac;
a3.3 Copy md5 checksum string, paste to "PKG_MD5SUM:=" in "./makefile/Makefile";
a3.4 Change "PKG_SOURCE_URL:=" to exactly http/ftp url;
a3.5 Save "Makefile";

STEP III
--------
Try cross-compile locally:
b1. "mkdir -p /openwrt/package/app-sample/";
b2. Copy "Makefile" in step a3.5 to dir made by step b1;
b3.1 "cd /openwrt/; make menuconfig", choose package in "Utilities" > "app-sample" (hit "Space" key), save & exit;
b3.2 "make package/app-sample/compile V=s";
b3.3 Fix your package dependencies;
b4. Check "cd /openwrt", "ls bin/ar71xx/packages/app-sample*";

STEP IV
-------
Submit to Admin. 
Every developer should submit these files:
c1. README.txt or CHANGELOG.txt;
c2. Archive file, named like "app-sample_1.0-1.tar.bz2";
c3.1 "Makefile" (from step a3.5): that you have verified locally.
c3.2 Upload to release url if needed; but DO change the url in "Makefile".

F.A.Q. & HELP
-------------
I'll keep this document updated.
Thanks guys.
Qige @ 2017.03.14
