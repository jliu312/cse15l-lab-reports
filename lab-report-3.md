# Lab Report 3
## Grep Command Options

### Recursively searches all files and sub-directories of a given directory (-R)
Searches in all the files in a given directory and all the files in a sub-directory.
- This is very useful when a high level search is performed across multiple directories.
```
$ grep -r "Chevrolets and Plymouths"

written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt:The presence of such architectural wonders, no matter how dilapidated, led UNESCO to declare Old Havana a World Heritage Site in 1982. In the central tourist quarter, an expanding number of buildings are being spruced up with the assistance of UNESCO and foreign foundations, but many others are propped up by wooden columns, lean-tos that appear to be merely forestalling the inevitable. Their arcades, fluted pillars, and mosaic tiles are teetering on last legs, praying for restoration miracles. At night the deep darkness of the streets is punctuated only by the neon glow of TV sets from tiny front rooms and the occasional headlights of a small colony of gas-guzzling vintage Chevrolets and Plymouths.
```
- In this case, we were in the parent directory of written_2. If "-r" were not used, we would only be searching the files immediately inside the workign directory and not all the files inside the sub-folders.

Another example: 
```
```

### Display only file names (-l)
Displays only the file names, rather than every chunk of text where the given string exists.
- This can be especially useful when you only want to know the file a word comes from

### Case Insensitive (-i)
Searches for any string that matches given string, case insensitive
- Example 1: 
```
$ grep -lr "lucayans" #Returns nothing
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

###
