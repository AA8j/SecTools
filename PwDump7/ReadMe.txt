========================================================================
       Pwdump version 7.1  - 07/01/2007
       Andres Tarasco Acuna atarasco_[at]_gmail.com
       http://www.514.es

========================================================================


Why another pwdump software?
-------------------------------------------
Every pwdump / samdump applications have their own way to work, 
for example creating services, inyecting code to lsass process however there
are always ways to stop that software for working like for example just disabling
administrative shares most pwdump applications will stop working.

However, pwdump7 works in a different way. This software works with their own
filesytem driver ( from rkdetector.com technology) so users with administrative 
privileges are able to dump directly from disk both SYSTEM and SAM registry hives.

Once dumped, the syskey key will be retrieved from the SYSTEM hive and then used to
decrypt both lanman and ntlm hashes and dump them in pwdump like format.


usage:
------

D:\>pwdump7.exe -h
Pwdump v7.1 - raw password extractor
Author: Andres Tarasco Acuna
url: http://www.514.es

usage:
 pwdump7.exe                              (Dump system passwords)
 pwdump7.exe -s <samfile> <systemfile>    (Dump passwords from files)
 pwdump7.exe -d <filename> [destionation] (Copy filename to destionation)
 pwdump7.exe -h                           (Show this help)


dump passwords:
----------------

D:\>PwDump7.exe
Pwdump v7.1 - raw password extractor
Author: Andres Tarasco Acuna
url: http://www.514.es

administrator:500:25FC25A0CA659E57ACEDB07452AB7A8E:6C1B3BE8D28CD3E7AB63122C8A572DDF:::
guest:501:0E175C3EFF8EED1652440321FCD91E4E:2850991451071A5B7A95F2977D4AAEF0:::
atarasco:1001:45C6AEEDC857A06DC595236F8F5FECAA:D0253497114C1B4CC337210F4580A716:::


dump locked file:
-----------------

D:\>PwDump7.exe -d c:\pagefile.sys pagefile.dmp
Pwdump v7.1 - raw password extractor
Author: Andres Tarasco Acuna
url: http://www.514.es

saving c:\pagefile.sys as pagefile.dmp
File pagefile.dmp saved


dump from alternate source:
---------------------------

d:\>pwdump7.exe -s c:\sam.dmp c:\system.dmp



TODO:
-----
This version is still beta and have some limitations but i will continue working on it

- password modification on the fly, updating SAM passwords. the changed password will work 
once the system is rebooted, and there will be no traces about account compromise.
- link with openssl libraries. This time you need the libeay32.dll lib in your path :)
- Add domain passwords support. At this time, domain passwords are stored at c:\windows\ntds\ntds.dit but the cipher is still unknown. If you have information about it, please contact me.



Changelog:
----------
v7.1 - Added Fat32 support
     - Added dumpfile support
     - Added support for alternative sam and system files (offline analysis)

v7.0 - first release, works with ntfs

