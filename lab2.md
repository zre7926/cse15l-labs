Lab Report 2 - Servers and SSH Keys (Week 3)
========
Ryan Zhang 

Part 1
--------
For this program, I used two files: `Server` and `ChatServer`. The implementation of `Server` is the same as the one in the [wavelet example](https://github.com/ucsd-cse15l-f23/wavelet). <br>Below is my implementation of `ChatServer`:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String output = "";
    public String handleRequest(URI url) {
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("&");
            output += String.format("%s: %s\n",parameters[1].substring(5),parameters[0].substring(2));
            return output;
        }
        return "404 Not Found!";
    }
}

public class ChatServer {
    public static void main(String[] args) throws IOException{
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```
<br>
I used `/add-message` twice:<br>
First Run:<br>
![First Run](images/run1.png)<br>
The `handleRequest` method is called with the argument being the url as an `URI` object. Within the if statement in that method, the `getPath` method, which has no argument, gets the path of the url (`/add-message?s=I like bagels&user=Bob`) and the `contains` method determines whether the path contains the argument, which is `"/add"`. Since the path does contain `"/add"`, the code in the `if` statement runs and the `getQuery` method is ran with no arguments, which gets the part of the path inside the query (`s=I like bagels&user=Bob`). Then, the `split` method splits that into `String` elements seperated by `"&"`s, which is the argument, and stores them into an array of `String`s (`["s=I like bagels", "user=Bob"]`). Then, the output `String` is concatenated with a new `String` that is created with the `String.format` method with arguments of the format (`"%s: %s\n"`) and the parts of the two parameters that the user wants to be displayed (`"I like bagels" and "Bob"`). This changes the `output` field to `"Bob: I like bagels\n"`

<br>
Second run:<br>
![Second Run](images/run2.png)
The `handleRequest` method is called with the argument being the url as an `URI` object. Within the if statement in that method, the `getPath` method, which has no argument, gets the path of the url (`/add-message?s=Me too&user=Jim`) and the `contains` method determines whether the path contains the argument, which is `"/add"`. Since the path does contain `"/add"`, the code in the `if` statement runs and the `getQuery` method is ran with no arguments, which gets the part of the path inside the query (`s=Me too&user=Jim`). Then, the `split` method splits that into `String` elements seperated by `"&"`s, which is the argument, and stores them into an array of `String`s (`["s=Me too", "user=Jim"]`). Then, the output `String` is concatenated with a new `String` that is created with the `String.format` method with arguments of the format (`"%s: %s\n"`) and the parts of the two parameters that the user wants to be displayed (`"Me too" and "Jim"`). This changes the `output` field to `"Bob: I like bagels\nJim: Me too\n"`

