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


All of the methods are called in this screenshot as I tried to make my code as minimal as possible. The relevent arguments in this screenshot would be `String[] args` in the main method in the StringServer class, and the `URI url` in the handleRequest method in the Handler class, which implements URLHandler. In the Handler class, the url is given to the handleRequest method where it checks the url to see if it has what we're looking for which is `/add-message`. If the url doesn't have it, then it will display `404 Not Found`. If the url does have `/add-message` the method will then split the string and store what is in each side of the equal sign. THe left half will go to the first element of `message` and the other half will go to the second element of `message`. So, the message we want to display is on the right end of the equals sign so we need to display the second element of `message`. 


Screenshot 2:


![image](https://user-images.githubusercontent.com/122564073/215426089-02f5c143-0132-4e37-a058-0d6493a44e73.png)


It's the same as the above screenshot, however in this one we test whether my code can take in spaces in the string.

## Part 2: Bugs in Lab 3


In my report, I will be discussing the `reverse` method.

The `reverse` method passed the initial test with an empty array to reverse. However when we tested it with a non-empty array, it failed.


Here is the test that passed:


````
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
````


Here is the test that failed:


````
    int[] input2 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input2));
````


What the `reverse` method did was return an empty array. That isn't what we want. 

We took a deeper look into the code and it seems that when the method created a new array,`newArray`, it would use the new array to fill the input array,`arr`, with zeros. The method did this because when `newArray` was created, its data wasn't initialized meaning its data was initialized to zero, and in the for-loop, it would fill the input array with newArray's data, which are zeros. 

Here is the image of the test cases:


![image](https://user-images.githubusercontent.com/122564073/215538778-4819b792-47a3-43f5-be6c-08f163bd6a04.png)


It was evident that the method was just returning zeros because `testReverse1` returned as a failure but not `testReverse2`. 


This was the code before making any changes:



````
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
````


And here is the code after making changes:


````
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
````

What we did was switch the assignment in the for-loop and return newArray instead of the input array. 

Now I tested the code with the same test cases but with the new code and the image below shows that `testReverse2` now fails but not `testReverse1` which is what we want.


![image](https://user-images.githubusercontent.com/122564073/215540849-0873b5fd-b66d-40e5-a2fc-010964dde4d7.png)


## Part 3 - What did I learn?

It may seem really irrelevent to the course, but coming into computer science as a woman, I thought it would be really difficult seeking help or looking for people to socialize in within the same major. It's hard finding a community within this major, especially a community of women. I often feel really isolated because of imposter syndrome. It feels like everyone around me know what's going on, but when it comes to me, I have absolutely no idea. But within Lab 2 and 3 in this class, I feel a lot more included. When we're working in groups, it feel like when we're lost, we're lost together. And we would seek help together and figure out the problem together. I learned that there *is* a community here for me. 


And if you want a more academic answer. I learned how to write test cases. Going through CSE11 and now CSE12 and CSE15L, I never really knew how to write test cases. Because we had to wrtie them in Lab 3, it really helped me not just in this class but now across all of my classes.
