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

When we first login using the password you found in last level. You find data.txt in the present directory.It was instructed to work in /tmp/any_arbit_dir. So let's just create a new directory and copy this file there.

```$mkdir /tmp/lvl1213 && cp data.txt /tmp/lvl1213```

now just migrate to the directory ```cd /tmp/lvl1213```

On doing ``` $file data.txt``` we get ```$data.txt: ASCII text```. Hint is this file has been repeatedly compressed and it is a hexdump of it. Let's just reverse hexdump it.

```$xxd -r data.txt > data```

```$file data```

```$data: gzip compressed data, was "data2.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix```

