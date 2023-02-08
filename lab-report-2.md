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
        } else {
          return str + "\nuse /add-message?s= to add to the string";
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
- This runs through the handleRequest() method and the first if statement since it has "/add-message"
- Then it goes through the next if statement since the first parameter is "s" 
- Then the str field is "hello \n"

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1068015468549521418/Screenshot_2023-01-25_at_7.52.05_PM.png)


**Adding "world"**
- Runs through the same path as previous URL request.
- Now, str field is "hello \n world \n"

![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067962336280858676/Screenshot_2023-01-25_at_4.20.59_PM.png)

## Part 2
<!-- Choose one of the bugs from lab 3.

Provide:

A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
Briefly describe why the fix addresses the issue. -->

### **The following tester method would fail the JUnit test.**
We would initially remove the smallest element (1.0), and the average should be (1.0 + 2.0 + 3.0)/3 = 2.0. However, the method returns 3.6666. This is because the method removes all doubles equal to the smallest element, so it removes both 1.0s, leading to the erroneous calculation.
```
double[] input1 = {1.0, 1.0, 2.0, 3.0};
assertEquals(2.0, ArrayExamples.averageWithoutLowest(input), 0.0);
```
### **Whereas this JUnit test would not induce a failure.**
This method does not induce a failure because there is only one instance of the smallest element, 1.0. Therefore, it will function correctly and get the correct 2.5 average.
```
double[] input2 = {1.0, 2.0, 3.0};
assertEquals(2.5, ArrayExamples.averageWithoutLowest(input2), 0.0);
```
Leads to this error from JUnit:
![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1067984955046633542/Screenshot_2023-01-25_at_5.50.48_PM.png)

The original buggy code was:
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
  ```

I fixed it to be:
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      sum += num;
    }
    sum -= lowest;
    return sum / (arr.length - 1);
  }
```
- I deleted the if statement within the for loop and then just subtracted the lowest number.
- The problem with the original code was that when there was that if there were two or more values that coincided with lowest, it would not include both of them.
- My fix includes all the values and subtracts the lowest so it will only remove one value

## Part 3
- Week 2 introduced me to the URIHandler interface in Java. I learned how to handle URI/URLs in Java and a simple overview of how they work with queries and other simple features.