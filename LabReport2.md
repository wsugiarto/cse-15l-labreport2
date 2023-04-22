# Lab Report 2
## String Server
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Try to use a /add-message?s=<string> path ");
        } 
        else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    message += parameters[1] + "\n";
                    return String.format(message);
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


Above are 2 screenshots and code from the StringServer, The screenshots show how the `/add-message?s=<String>` feature works in the web server. In both cases, they both call on String handleRequest(URI url) method, which takes the url of the website as the argument. In both, the method takes note that the path is `/add-message`, so it checks for the query and splits it into an array named parameter to check seperate the string into elements seperated by the `=`. The array has two elements one before the = and one after. In both screenshots, since the first element is `s` then the second element will be added to the string variable `message` together with `\n` to print a new line. For the first screenshot, message was updated to `"My name is" + "\n"`, then in the second screenshot it was updated to `"My name is" + "\n" + "Wilson Sugiarto" "\n"`. The message variable is updated whenever


Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
