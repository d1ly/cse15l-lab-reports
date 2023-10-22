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

