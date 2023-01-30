# Lab Report 2 - Servers and Bugs

## Part 1: Creating `StringServer.java`

Here is my code:

````
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler{
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String[] message = url.getQuery().split("=");
            return message[1];
        }else{
            return "404 Not Found!";
        }
    }
}


class StringServer{
    public static void main(String[] args) throws IOException{
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
````

Screenshot 1:

![image](https://user-images.githubusercontent.com/122564073/215426187-8222256d-0f93-4ff5-9e38-cc507b2dd9ac.png)


Screenshot 2:

![image](https://user-images.githubusercontent.com/122564073/215426089-02f5c143-0132-4e37-a058-0d6493a44e73.png)


