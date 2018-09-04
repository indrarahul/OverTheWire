# Bandit Level 12 → Level 13

> # Level Goal
> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly
> compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example:
> mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

> # Commands you may need to solve this level
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv

> Helpful Reading Material
> Hex dump on Wikipedia

## Solution

When we first login using the password you found in last level. You find data.txt in the present directory.

On doing ```bash $file data.txt```  
