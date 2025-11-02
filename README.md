# Bash + Python
- Python: `with open('filename.txt', 'mode') as file_object:` recommended and safest way to handle file operations as it **closes the file automatically** after use
- Linux: `mv original_filename {,_extended_filename}` results in the **final filename** as *`original_filename_extended_filename`*
- Python: Simply converting a file with numbers(string format) to actually int numbers
  > ![John Hammond PicoCtf2022 #2](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/pic1.png)
- Linux: `grep "TEXT" file` searches for TEXT in file `file filename` gives the type of file along with a short description `unzip files.zip` to unzip a file `.` means current directory `find . -name file.txt` searches recursively for file.txt, and prints the full path to every match.
- `grep -r "text"` will search for text everywhere including subdirectories within a directory || **-r for recursive**
- `unzip` command unzips a *.zip* file and the output is the og zip file along with multiple unzipped files **BUT** `gunzip` command unzips a *.gz* file and the og .gz file is deleted and replaced witha single unzipped file. `zcat .gz_file >/tmp/disk` will do the same operation as gunzip but extracts to a specified file in a directory (same as `gunzip -c .gz_file >/tmp/disk`)
- Python: `reversed(list1)` will return a reversed iterator, use `for i  in reversed(list1)` to traverse list backwards, to make it reversed new list: `list(reversed(list1))`
- Python: To access and pass arguments to a program using CLI
  > ![Python Code screenshot](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-03%2001_26_08-NVIDIA%20GeForce%20Overlay.png)
- Python: **ASCII**: *Decimal*: 65(A) ; 97(a) :: *Hexadecimal*: 41(A):5A(Z) ; 61(a):7A(z)
- Python: Using the escape sequence `\x` will interpret **2 numbers** after it as Hex characters. Ex: `print("\x43\x41")` will print **CA**
- Python: `python -c 'print("\x5F\x42\x5F")'` is the shortcode syntax for using python in CLI. The program outputs **\_B_**
 ----
# THE SELUTH KIT
+ ***mm*** : All tools prepended with mm operate on disk lvl with minimal guidance from operator. The media layer doesnt provide much info about the data contained in the disk image. Ex: `mmls [options] <disk_image>` -> used to list and view the partition layout of a disk or disk image
+ ***blk*** : Block layer is the numbers of the disk image broken into equal-sized chunks. A single file is likely to contain multiple blocks. Ex: `blkcat [options] <image> <blk_address>` -> used to display/extract the raw contents of specific blocks (sectors) from a disk image.
+ ***i*** : An inode is a structure that stores all the metadata about a file (except its name) and points to the blocks containing its actual data. Ex: `icat [options] <image> <inode>` -> used to extract or display the contents of a file from a disk image, using its inode number.
+ ***f*** : Filename layer, where most users interact. Ex: `fls [options] <image>`-> lists files and directories (including deleted ones) from a disk image and shows their inode numbers.
+ EX: `fls -o 360448 disk.flag.img 451` will list files and dir in *disk.flag.img* with offset (**-o**) [obtained using `mmls`] and inode 451 [obtained using `fls -o 360448 disk.flag.img`]

----

# Python Errors
- `ZeroDivisionError` : Trying to divide by 0
- `ValueError` : Wrong value type entered. Ex: float("hello") **OR** if a user enters a string where they were supposed to enter another data type

----
