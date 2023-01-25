# Lab Report 2 

## Part 1
<!-- Show the code for your Simplest Search Engine from week 2 (use a code block in Markdown). Then, show three screenshots of using it including at least one add and one query, showing the URL in the browser and the response on the page.

For each screenshot, describe:

Which methods in your code are called
What the values of the relevant arguments to those methods are, and the values of any relevant fields of the class
If those values change, how they change by the time the request is done processing --> 

### **Here's my code for my simple search engine:**

```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    Set<String> strings = new HashSet<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("use /add?s= to add a new string to the list, /search?s= to search for all strings that contain that substring.");
        }
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                strings.add(parameters[1]);
                return String.format("Added %s", parameters[1]);
            }
        } else if (url.getPath().contains("/search")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                return searchForString(parameters[1]).toString();
            }
        } 
        return "404 Not Found!";
    }

    public List<String> searchForString(String keyword) {
        ArrayList<String> matches = new ArrayList<>();
        for(String s : strings) {
            if(s.contains(keyword)) {
                matches.add(s);
            }
        }
        return matches;
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
### **Here's an example use of my simple search engine:**
All of the following URL requests go through the handleRequest(URI url) method

**Adding "pineapple" to the list**
- This runs through the "add" if statement and adds to the strings ArrayList field. 
- Now, strings contains [apple]

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067650441531363368/Screenshot_2023-01-24_at_7.41.37_PM.png)


**Adding "apple" to the list**
- Runs through the same path as previous URL request.
- Now, strings contains [apple, pineapple] 

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067650481394036756/Screenshot_2023-01-24_at_7.41.48_PM.png)

**Search for keyword "app"**
- Runs through the last if statement for the "search," which calls the searchForString method
- Returns and displays the strings that contain given substring, whcih is [apple, pinapple]

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067650538889560125/Screenshot_2023-01-24_at_7.42.01_PM.png)
