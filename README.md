# Bash + Python
- Python: `with open('filename.txt', 'mode') as file_object:` recommended and safest way to handle file operations as it **closes the file automatically** after use
- Linux: `mv original_filename {,_extended_filename}` results in the **final filename** as *`original_filename_extended_filename`*
- Python: Simply converting a file with numbers(string format) to actually int numbers
  > ![John Hammond PicoCtf2022 #2](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/pic1.png)
- Linux: `grep "TEXT" file` searches for TEXT in file `file filename` gives the type of file along with a short description `unzip files.zip` to unzip a file `.` means current directory `find . -name file.txt` searches recursively for file.txt, and prints the full path to every match.
- `grep -r "text"` will search for text everywhere including subdirectories within a directory || **-r for recursive**
- `unzip` command unzips a *.zip* file and the output is the og zip file along with multiple unzipped files **BUT** `gunzip` command unzips a *.gz* file and the og .gz file is deleted and replaceed witha single unzipped file.
- `mmls` command is a part of **THE SELUTH KIT** that displays the partition layout of a disk image, showing information like partition tables, unallocated space, and partition offsets.
