# Lab Report 5
## **`Find` Command Options**

### **Search for a specific type: `-type`**
Searches for files of a specific type. \
`d` is for directories, `f` for regular files, `l` for symbolic links, and `c` for character devices.

```
$ find written_2 -type d

written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```

- Here, find returns all the subdirectories of written_2 and all of its subdirectories, with `type -d` which can be useful in seeing directories hidden deep within a folder.

Another example: 

```
$ find written_2/non-fiction/OUP/Abernathy -type f 

written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt

```

- Here, I searched for only files with `-type f`. This can be useful to list all the files in a directory, without listing its subdirectories. 

### **Searching by last modified time: `-mtime`**
Searches for files based on their modification time
- Can be useful to find recently editted files. 

```
$ find written_2 -mtime -7
written_2/travel_guides/berlitz2/Cuba-History.txt

```
- `-mtime -7` attempts to search for files editted in the last 7 days. This shows that I recently editted the file `Cuba-History.txt`.
- Makes it easy to see files changed within a directory.

```
$ find written_2 -mtime +7
written_2/travel_guides/berlitz2/Cuba-History.txt

written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Berk/ch2.txt
...

#Continues to list all the files and subdirectories of written_2
```

- Since most files have not been editted recently, all files except for `Cuba-History.txt` is listed with the extra option of `mtime +7`, indicating the `find` command to search for everything last editted in *more* than 7 days.

### **Search by size: `-size`**
Searches for files by size
- Here's an example:

```
$ find written_2 -size +200k

written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
```

- This looks for all files greater than 200 kilobytes, which returns only 3 files. 

- Another example, but this time with `-`

```
$find written_2 -size -800c

written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1/HandRIbiza.txt
```
- This returns everything less than 800 bytes (bytes represented with `c`). 
- This can be useful to find extremely large or small files within a directory.

### **Setting a maximum depth: `-maxdepth`**
Searches recursively only to a certain defined depth of sub-directories (including itself)

```
$ find written_2 -maxdepth 2 -name '*.txt'

#returns nothing
```

- In this case, there are no files within `written_2` and its immediate subdirectories, so there is nothing returned.

```
$ find written_2 -maxdepth 3 -name '*.txt'

written_2/travel_guides/berlitz1/HandRLasVegas.txt
written_2/travel_guides/berlitz1/HistoryJapan.txt
written_2/travel_guides/berlitz1/IntroMalaysia.txt
written_2/travel_guides/berlitz1/HandRIstanbul.txt
written_2/travel_guides/berlitz1/HistoryJamaica.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
#continues with all files...
```
- In this case, all the files are within 3 directories deep, so they are all returned.

- This can be useful to limit searching in deep folders that will take up a lot of time and compute.