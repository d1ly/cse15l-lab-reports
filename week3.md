# CSE15L Week 3 Lab Report - VSCode and Your Local Machine

# Code for StringServer.java
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.List;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    List<String> listOfStrings = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("This is the homepage. Use /add-message");
        }
        else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String message = parameters[1];
                    listOfStrings.add(message);
                    StringBuilder output = new StringBuilder();

                    for (int i = 0; i < listOfStrings.size(); i++) {
                        output.append((i + 1) + ". " + listOfStrings.get(i) + "\n");
                    }

                    return output.toString();
                }
            }
            return "404 Not Found!";
        }
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

#Using add-message/

![Image](string1.PNG)

The method first called within the class Handler is `handleRequest` which takes in the URL as an argument. Then it checks the path of the URL and if it contains "\add-message" which is true. It then gets the query of the URL and splits it into two parameters before and after the `=`, checking if `s` is the first parameter. Then the second parameter, in this case is "Hello" will then be added into the array list of strings. A StringBuilder is declared to help return an output to the website, and a for loop is done to build the output to finally return.



![Image](string2.PNG)


#Part 2: SSH keys and password

