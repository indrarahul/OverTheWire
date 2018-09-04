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

```$file data```<br>
```data: gzip compressed data, was "data2.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix```
From here it takes time. You basically have to do ```$file file_name``` check the file, rename it and unzip/untar/unbiz2/ungzip using proper tools.

so let's just rename this file to gz ```$mv data data.gz``` ungzip it ```$gzip -d data.gz```. You will get a file named data.

```$file data```<br>
```data: bzip2 compressed data, block size = 900k```

Repeat the process
```$mv data data.bz2```<br>
```$bzip2 -d data.gz```<br>

```$file data```<br>
```data: gzip compressed data, was "data4.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
```
<br>

```$mv data data.gz```<br>
```$gzip -d data.gz```<br>

```$file data```<br>
```data: POSIX tar archive (GNU)```<br>

```$mv data data.tar```<br>
```$tar xvf data.tar```<br>

```$file data5.bin```<br>
```data5.bin: POSIX tar archive (GNU)```<br>

```$mv data5.bin data5.tar```<br>
```$tar xvf data5.tar```<br>

```$file data6.bin```<br>
```data6.bin: bzip2 compressed data, block size = 900k```<br>

```$mv data6.bin data6.bz2```<br>
```$bzip2 -d data6.bz2```<br>

```$file data6```<br>
```data6: POSIX tar archive (GNU)```<br>

```$mv data6 data6.tar```<br>
```$tar xvf data6.tar```<br>

```$file data8.bin```<br>
```data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix```<br>

```$mv data8.bin data8.gz```<br>
```$gzip -d data8.gz```<br>

```$file data8```<br>
```data8: ASCII text```<br>

Oooof !! Finally You got something let's just do ```$cat data8 quickly``` .... and ...

Ta daah.
```The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL```<br>


Happy Hacking l33t5






