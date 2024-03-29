# Part 1
## Codes
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String user_message = "";
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            //display current user:message
            return user_message;
        } else {
            if (url.getPath().contains("/add-message")) {
                //[s, How are you&user, yash]
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String new_message = parameters[1].split("&")[0];
                    String user = parameters[2];
                    String current_message = String.format("%s: %s\n", user, new_message);
                    user_message = user_message + current_message;
                    return user_message;
                }
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
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
## Add Message 1
 <img src="lab2sc1.png" width="800" />

 
1) In my code, method **handleRequest** of the **Handler** class is called.
2) The relevant arguments are: ```URI url```, the URL object of the request, it is ```"/add-message?s=Hello&user=jpolitz"```. Values of relevant fields of **Handler** class are ```user_message```.
3) ```user_message``` changes everytime add-message is called, before any method is called, it is an empty string. After add-message is called, it is updated with the new user and message ```jpolitz: Hello```.


 
## Add Message 2
<img src="lab2sc2.png" width="800" />


1) In my code, method **handleRequest** of the **Handler** class is called.
2) The relevant arguments are: ```URI url```, the URL object of the request, it is ```"/add-message?s=TeeHee&user=Zoey"```. Values of relevant fields of **Handler** class are ```user_message```.
3) ```user_message``` changes everytime add-message is called, before any method is called, it is a string with ```"jpolitz: Hello"```. After add-message is called, it is updated with the new user and message:
```Zoey: TeeHee``` which becomes ```"jpolitz: Hello\n Zoey:TeeHee"```.

## Current Page
![Image3](lab2sc3.png)


---

# Part 2
**absolute path to private key & public key for SSH key for ```ieng6```**
> The one end with. pub is public and the first one is private
![Imageprivate](lab2private.png)
> The absolute path where public key is located in ieng6
![waaa](lab2revise.png)
/home/linux/ieng6/oce/25/jih084/.ssh/authorized_keys
**Log in without being asked for a passward**
![Imagelogin](lab2login.png)

---

# Part 3

In week 2 and 3, I learned about the structure of URL and how to code a files handling the requests, I am more confident with websites now. I also learned new commands such as ```ssh```. I also learned about Debugging and the importance of having a good attitude when programming from the assigned readings. 
