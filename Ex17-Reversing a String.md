# Ex17 Reversing a String Using Stack Data Structure

## DATE:
16.11.2025  

## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.  
2. Create an empty stack of characters.  
3. Traverse the string and push each character onto the stack.  
4. Pop each element from the stack and append it to a new string.  
5. Display the reversed string.  
6. Stop the program.  

## Program:
```java
/*
Program to reverse an input string using a stack
Developed by: Kishore B
RegisterNumber: 212224100032
*/
import java.util.*;

public class ReverseStringStack {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a string: ");
        String str = sc.nextLine();
        Stack<Character> stack = new Stack<>();
        for (char ch : str.toCharArray())
            stack.push(ch);

        StringBuilder reversed = new StringBuilder();
        while (!stack.isEmpty())
            reversed.append(stack.pop());

        System.out.println("Reversed string: " + reversed.toString());
        sc.close();
    }
}
```
## OUTPUT
<img width="943" height="88" alt="image" src="https://github.com/user-attachments/assets/95e7e65b-68e6-46eb-9baf-880924d43be9" />

## RESULT
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.
