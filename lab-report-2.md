# Lab Report 2 

## Part 1
<!-- Show the code for your Simplest Search Engine from week 2 (use a code block in Markdown). Then, show three screenshots of using it including at least one add and one query, showing the URL in the browser and the response on the page.

For each screenshot, describe:

Which methods in your code are called
What the values of the relevant arguments to those methods are, and the values of any relevant fields of the class
If those values change, how they change by the time the request is done processing --> 

### **Here's my code for my StringServer:**

```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                str = str + parameters[1] + "\n";
            }
        } 
        return str;
    }
}

class StringServer {
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

**Adding "hello"**
- This runs through the handleRequest() method and the first if statement
- Now, str is "hello \n"

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067962310271967333/Screenshot_2023-01-25_at_4.20.51_PM.png)


**Adding "world"**
- Runs through the same path as previous URL request.
- Now, str is "hello \n world \n"

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067962336280858676/Screenshot_2023-01-25_at_4.20.59_PM.png)

