# Lab Report 3
## **Grep Command Options**

### **Recursively searches all files and sub-directories of a given directory (-r)**
Searches in all the files in a given directory and all the files in a sub-directory.
- This is very useful when a high level search is needed across multiple sub-directories.

```
$ grep -r "Chevrolets and Plymouths"

written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt:[...] At night the deep darkness of the streets is punctuated only by the neon glow of TV sets from tiny front rooms and the occasional headlights of a small colony of ]]gas-guzzling vintage Chevrolets and Plymouths.
#I truncated the actual return value
```

- In this case, we were in the parent directory of written_2. If "-r" were not used, we would only be searching the files immediately inside the workign directory and not all the files inside the sub-folders.

Another example: 

```
$ grep -r "Lucayans"

written_2/travel_guides/berlitz2/Bahamas-History.txt:[...]Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba. #text truncated again

written_2/travel_guides/berlitz2/Bahamas-History.txt:[...] As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean. #text truncated
```

- Again, the "-r" option tells grep to recursively search through all the sub-files and we are only able to find the instance of "Lucayans" that way.

### **Display only file names (-l)**
Displays only the file names, rather than every chunk of text where the given string exists.
- As seen from the "-r" examples, sometimes the returned values can be very long and difficult to read.
- The "-l" option can be especially useful when you only want to know the file a word comes from.
- Using one of the previous examples with the addition of the "-l" option:

```
$ grep -lr "Lucayans"

written_2/travel_guides/berlitz2/Bahamas-History.txt
```

- Makes it a lot shorter and easier to read, especially if we only want the file names.
- Here's another example; if we were to omit the "-l" option, it would be extremely long

```
$ grep -lr "Bahamas" 

written_2/travel_guides/berlitz1/WhatToFWI.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
```

- Imagine multiple lines for each file highlighting where the text is, especially for files with mulitple instances of the text(or try it yourself without the "-l")

### **Case Insensitive (-i)**
Searches for any string that matches given string, case insensitive
- Example 1: 

```
$ grep -lr "lucayans" #returns nothing
```

- Whereas: 

```
$ grep -lri "lucayans"

skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz2/Bahamas-History.txt
```

- Returns the correct path. The inclusion of "-i" is extremely helpful when the user does not know the capitalization of the string that is being searched for.

- Here's another example of "-i" being useful: 

```
$ grep -lr  "hello"

skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz1/WhereToHongKong.txt
skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz1/WhereToItaly.txt
```

- Versus:

```
$ grep -lri  "hello"

skill-demo1-server/skill-demo1-data/written_2/non-fiction/OUP/Berk/CH4.txt
skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz1/WhereToFrance.txt
skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz1/WhereToHongKong.txt
skill-demo1-server/skill-demo1-data/written_2/travel_guides/berlitz1/WhereToItaly.txt
```

- In this case, the "-i" is useful since it allows the user to only need one command to search for all capitalizations of a word. 
- In the grep without "-i", some many capitalizations are omitted. 

