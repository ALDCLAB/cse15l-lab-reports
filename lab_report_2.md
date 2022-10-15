
# Lab Report 2 #  
## The World's Simplest Search Engine ##  
Here is my code for the SearchEngine assignment. 


```
public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Hello!");
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if(parameters[0].equals("s")) {
                    search.add(parameters[1]);
                    return String.format(parameters[1]);
                }
            }
            else if (url.getPath().contains("/search")) {
                String[] parameters = url.getQuery().split("=");
                if(parameters[0].equals("s")) {
                    for (i = 0; i < search.size() - 1; i++) {
                        temp = search.get(i);
                        if(temp.contains(parameters[1])) {
                            containSearch.add(temp);

                        }
                    }
                    searchResult = containSearch.toString();
                    return String.format(searchResult);
                }
            return "404 Not Found!";
            }
        }
        return "Hello!";
    }
}
```  

![Image](Screenshots/firstadd.PNG)  
With `/add?s=word` added to the URL, it goes thru the if statement, denys the first if statement, since the URL path does not only equal "/."  

It then goes to the else statement where it checks the first if statement inside, and see if the url contains "/add." When that is true (which it is in the screenshot), it splits the next url lines when there is a "=." It then puts the strings in an array called parameters.  

It then goes to another if statement checking the first split string is equal to "s." If it does, it adds the second split string to search, which is an array list. This array list named search is responsible for storing all the words added. This will help our search function whn it is used later.  

That is the entire add function of this searchEngine. 

![Image](Screenshots/secondadd.PNG)  
![Image](Screenshots/thirdadd.PNG)  
For this example, I also added these words in order to demonstrate the search function. The same methods are called, and they join apple along in the ArrayList. 

![Image](Screenshots/searchenginetest.PNG)  
For the search function, it checks if the url contains "/search" in it. 
If it does, it does the same parameter stuff just like the add if statement discussed earlier.  

It then goes to a for loop, looping the number of `search.size - 1` For every index inside of the search array (which is dependent on how many you added), the temp variable is assigned to it, which then is used to see if that index of temp contains the words of `parameters[1]` (Your desired search word). 

If the temp variable has it, it is added to another array list called `containSearch`. This repeats until each word in the search array is checked if they have contained the search word.  

Then the final part of the search statement is that it turns the array of the words added that has the word search (containSearch) and turns it into a string, and then returns it to the site to be seen. 
---  

## Debugging ##  
![Image](Screenshots/failureinducingtest.PNG)  
The test code.  
![Image](Screenshots/symptomtest.PNG)  
The failing test output of those two tests.  
![Image](Screenshots/bugfixneeded.PNG)  
The code bug, specifically the `arr[i] = arr[arr.length - i - 1];` line.  
![Image](Screenshots/bugfixtest.PNG)  
The new code to fix the bug.  
The problem with the original code was that when you reach a certain point of your array that is big (atleast a size of 2 or 3), it would try to assign the number of an index that has already changed. In my example code, the first test, when it trys to change index 2 into 1, it could not as index 0 was already assigned 3. This is why the beginning part of the array is fine but leaning towards the end it was not. 

![Image](Screenshots/failureinducingtest2.PNG)    
The test code.  
![Image](Screenshots/symptomtest2.PNG)  
The error.  
![Image](Screenshots/bugfixneeded2.PNG)  
The code needed to be fixed.  
![Image](Screenshots/bugfixtest2.PNG)  
The fixed code.  
The code that needed to be fixed was assigning the original array instead of the new array that needed to returned. It also returned the wrong array. This made it so the newArray was not getting assigned at all and wasn't even the result. 








