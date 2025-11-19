# Bash + Python
- Python: `with open('filename.txt', 'mode') as file_object:` recommended and safest way to handle file operations as it **closes the file automatically** after use
- Linux: `mv original_filename {,_extended_filename}` results in the **final filename** as *`original_filename_extended_filename`*
- Python: Simply converting a file with numbers(string format) to actually int numbers
  > ![John Hammond PicoCtf2022 #2](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/pic1.png)
- `zip file.zip file.txt` will zip "file.txt" and create a new **.zip** file called *file.zip* on the other hand if we need to zip a directory we need to use **`-r`** flag like `zip -r dir.zip dirname` this will recursively zip all subdirs as well as files inside of "dirname" if we don't use the **`-r`** flag then the subdirs will not be properly zipped.
- Linux: `grep "TEXT" file` searches for TEXT in file `file filename` gives the type of file along with a short description `unzip files.zip` to unzip a file `.` means current directory `find . -name file.txt` searches recursively for file.txt, and prints the full path to every match.
- Linux: `grep -r "text"` will search for text everywhere including subdirectories within a directory || **-r for recursive**
- Linux: `unzip` command unzips a *.zip* file and the output is the og zip file along with multiple unzipped files **BUT** `gunzip` command unzips a *.gz* file and the og .gz file is deleted and replaced witha single unzipped file. `zcat .gz_file >/tmp/disk` will do the same operation as gunzip but extracts to a specified file in a directory (same as `gunzip -c .gz_file >/tmp/disk`)
- Python: `reversed(list1)` will return a reversed iterator, use `for i  in reversed(list1)` to traverse list backwards, to make it reversed new list: `list(reversed(list1))`
- Python: To access and pass arguments to a program using CLI
  > ![Python Code screenshot](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-03%2001_26_08-NVIDIA%20GeForce%20Overlay.png)
- Python: **ASCII**: *Decimal*: 65(A) ; 97(a) :: *Hexadecimal*: 41(A):5A(Z) ; 61(a):7A(z)
- Python: Using the escape sequence `\x` will interpret **2 numbers** after it as Hex characters. Ex: `print("\x43\x41")` will print **CA**
- Python: `python -c 'print("\x5F\x42\x5F")'` is the shortcode syntax for using python in CLI. The program outputs **\_B_**
- Python: `ord(character)` is used to convert a character to its unicode value and `chr(integer)` converts the unicode integer back to its corresponding character.
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

# HTML & JS
- HTML & JS are executed in the **browser**
- Inputting a number and showing the result as number + 10
  >![](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/htmlcode.png)  ![](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-03_15-46.png)

----

# PHP
- In a file with the extension `*.php` we can mix html, JavaScript, and PHP code! If the server supports PHP, everything inside <?php ?> will be understood as PHP code and run by the **server**, not by the browser.
- Code in `*.php` to view time and run js code
  >![](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-04%2018_45_35-NVIDIA%20GeForce%20Overlay.png)
- for `date("h:i:s a");`: `h`: hour in 12 hr format `H`: hour in 24 hr format `i`: minutes `s`: seconds `a`: am/pm (Note that `m` shows month in numerical and `M` shows month in Letters)
----

# Croxx Site Scripting (XSS)
- XSS means attacker injects and executes their JavaScript on someone else’s browser through a vulnerable website allowing them to steal data, cookies and perform other actions.
> **COOKIES**
> - A small **TEXT FILE** that a website stores on your device to remember information about you.
> - When we revisit the same site, the browser resends the cookie back to the server for recognising us.
> - Cookies do Session Management(like keeping us signed in), Personalization(like theme), tracking our browsing behaviour for ads.
- Only using cookies for authentication will open the possibility of **Cross Site Request Forgery (CSRF).**
> ![](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-07%2014_02_18-NVIDIA%20GeForce%20Overlay.png)
> - `<script src="https://code.jquery.com/jquery-3.4.1.min.js"> </script>` line makes jQuery available to use in the HTML page.
> - `$.get("server name",{key:value},function(data){//Runs only on HTTP200(success)});` : `$.get()` asks the server for data → waits silently → if the server replies successfully → runs your function with success code.

----

# Cryptography
- Achieves **Confidentiality**(unintended can't read message) **Integrity**(message tampering should be detectable) **Authentication**(identity of a person can be verified accurately) **Non-Repudiation**(if someone sent a message, they can't deny the message was sent by them)
-  `zip --encrypt -r dir.zip dirname` will zip and encrypt using an older algorithm: **ZipCrypto**, which can be decrypted using `unzip dir.zip` using the *same password*
-  **Types of Ciphers**:
- - *Substution Ciphers*
    > It works by replacing each symbol in the plaintext with another symbol according to a fixed rule or key.
    > - **Monoalphabetic**: Each plaintext letter maps to a single fixed ciphertext letter. Ex: Ceaser Cipher.
    > - **Polyalphabetic**: Uses multiple substitution alphabets(the substitution changes after each letter, based on a key). Ex: Vigenère Cipher
    > - **Homophonic**: Maps one plaintext symbol to multiple possible ciphertext symbols.
- - *Transposition Ciphers*
    > Reorders the message instead of replacing its letters.
    > - **Rail Fence Cipher**: Letters are written in a zigzag pattern and then read row by row to get the ciphertext.
    > - **Columnar Transposition**: Message is written in rows under columns labeled by key numbers, then columns are read in key order to get the ciphertext.
    > - **Double Transposition**: The columnar transposition is applied twice.
    > - **Permutation Cipher**: Uses a fixed permutation pattern for rearranging blocks of text.
- ### Modern Cryptography
> - **Symmetric Cryptography**
>> - Same keys for encryption and decryption.
>> - Ex: **Advanced Encryption Standard (AES)**:
>>> - Combination of substitutions and transpositions using a key of fixed length(128 bit **OR** 256 bit)
>>> - **ECB(Electronic Code Book) operation mode:**
>>>> -  If using AES 128, we break the clear text in chunks of 128 bits and use AES to encrypt them independently.
>>>> -  Problem of leaking structure in the encrypted text.
>>>> -  If same message is resent, an attacker can see that the same message is being sent again.
>>>> -  **NOT RECOMMENDED**
>>> - **CBC(Cipher Block Chaining) operation mode:**
>>>> - Additional elements included such as **initialization vector**(a random value with the same size as the key, different for every message). Before starting the encryption, we do **XOR** between the **first block of cleartext** and the **Initialization Vector**, *Initialization vector is attached with the message once after encryption*, **we do not encrypt blocks independently**, but we use the encrypted text from one block and XOR it with the next block of cleartext we want to encrypt. Then, we use AES and the key to encrypt that result.
>>>>> ![](https://github.com/CBSINHA/Linux-Cybersecurity-ShortNotes/blob/main/Picture%20Uploads/2025-11-09%2019_54_10-NVIDIA%20GeForce%20Overlay.png)
>>> - Cleartext must be the same size as a multiple of the block size, for that we add padding, **PKCS #7** is standard.Ex: using **AES128**, block size is 128bits or 16bytes, if our cleartext has 12 bytes then we need padding of +4 bytes, the final cleartext with pad will be: **"12byte_message"+"\x04\x04\x04\x04"**, if 15 byte message then final message with pad:  **"15byte_message"+"\x01"**
> - **Asymmetric Cryptography**
>> - **Public key** for encryption and **Private key** for decryption
>> - Ex: **Rivest-Shamir-Adleman (RSA)**:
>>> - RSA public key: Pair of numbers (*e,n*) ; Private Key: Pair of numbers (*d,n*) ; Message(*m*) ; Ciphertext(*c*)
>>> - Encryption: **m<sup>e</sup> mod n=c** Decryption: **c<sup>d</sup> mod n=m**
>>> - **The KEY GENERATION Algorithm :**
>>>> - Take 2 large co-prime numbers **p** and **q**
>>> - RSA is considered secure only if the key is a number that would take at least 2048 bits(617 digits).
>> - Used for ***digital signatures*** (**private key** is used to encrypt a hash of the data, signer's **public key** can then be used to decrypt ensuring authenticity, integrity and non-repudiation)

----
