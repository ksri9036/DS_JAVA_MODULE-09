# Ex16 Check for Balanced Parentheses Using Stack

## DATE:
16.11.2025  

## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.  
2. Create an empty stack.  
3. Traverse each character in the string.  
4. Push opening brackets onto the stack.  
5. When a closing bracket is encountered, check if it matches the top of the stack.  
6. If any mismatch or leftover element exists, the parentheses are not balanced.  
7. If the stack is empty at the end, the parentheses are balanced.  

## Program:
```java
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: Kishore B
RegisterNumber: 212224100032
*/
import java.util.*;

public class BalancedParentheses {
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();
        for (char ch : str.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (stack.isEmpty()) return false;
                char top = stack.pop();
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '['))
                    return false;
            }
        }
        return stack.isEmpty();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter expression: ");
        String expr = sc.nextLine();
        if (isBalanced(expr))
            System.out.println("Balanced");
        else
            System.out.println("Not Balanced");
        sc.close();
    }
}
```
## OUTPUT 
<img width="950" height="93" alt="image" src="https://github.com/user-attachments/assets/353eb46e-654a-4d9d-9861-f94d885d80a8" />

## RESULT
Thus, the program correctly checks whether an input string has balanced parentheses using a stack.

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


# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)

## DATE:
16.11.2025  

## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.

## Algorithm
1. Start the program.  
2. Create a `Node` class with `data` and `next` attributes.  
3. Implement a `Queue` class with `enqueue()` and `dequeue()` methods.  
4. Enqueue customers (represented by integers or names).  
5. Dequeue each customer in FIFO order as they are served.  
6. Display the queue before and after serving customers.  
7. Stop the program.  

## Program:
```java
/*
Program to simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: Kishore B
RegisterNumber: 212224100032
*/
class Node {
    String data;
    Node next;
    Node(String data) {
        this.data = data;
        this.next = null;
    }
}

class Queue {
    Node front, rear;
    
    void enqueue(String data) {
        Node newNode = new Node(data);
        if (rear == null) {
            front = rear = newNode;
            return;
        }
        rear.next = newNode;
        rear = newNode;
    }

    void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        System.out.println(front.data + " has been served.");
        front = front.next;
        if (front == null)
            rear = null;
    }

    void display() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        Node temp = front;
        System.out.print("Current Queue: ");
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class TicketCounter {
    public static void main(String[] args) {
        Queue q = new Queue();
        q.enqueue("Alice");
        q.enqueue("Bob");
        q.enqueue("Charlie");
        q.enqueue("Diana");
        q.display();
        q.dequeue();
        q.display();
    }
}
```
## OUTPUT
<img width="950" height="125" alt="image" src="https://github.com/user-attachments/assets/9d85a3e2-357d-4d62-ba4b-0241b85d7cc3" />

## RESULT
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.

# Ex19 Palindrome Check Using Deque

## DATE:
16.11.2025  

## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1. Start the program.  
2. Read the input string from the user.  
3. Remove all non-alphanumeric characters and convert the string to lowercase.  
4. Use a deque to store characters of the string.  
5. Compare characters from both ends of the deque.  
6. If all pairs match, it’s a palindrome; otherwise, it’s not.  
7. Display the result.  

## Program:
```java
/*
Program to check whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: Kishore B
RegisterNumber: 212224100032
*/
import java.util.*;

public class PalindromeDeque {
    public static boolean isPalindrome(String str) {
        Deque<Character> deque = new LinkedList<>();
        for (char c : str.toCharArray()) {
            if (Character.isLetterOrDigit(c)) {
                deque.add(Character.toLowerCase(c));
            }
        }

        while (deque.size() > 1) {
            if (deque.removeFirst() != deque.removeLast())
                return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a message: ");
        String message = sc.nextLine();
        if (isPalindrome(message))
            System.out.println("Palindrome");
        else
            System.out.println("Not a Palindrome");
        sc.close();
    }
}
```
## OUTPUT
<img width="951" height="84" alt="image" src="https://github.com/user-attachments/assets/f2b651f4-310f-47eb-90dc-7394b64e0602" />

## RESULT
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.


# Ex20 Sorting an Array using Merge Sort Algorithm

## DATE:
16.11.2025  

## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.

## Algorithm
1. Start the program.  
2. Divide the array into two halves using recursion.  
3. Continue dividing until each subarray contains a single element.  
4. Merge the subarrays in sorted order using a helper merge function.  
5. Return the fully sorted array.  
6. Display the sorted array.  

## Program:
```java
/*
Program to sort a given array of integers in ascending order without using built-in sorting functions
Developed by: Kishore B
RegisterNumber: 212224100032
*/
import java.util.*;

public class MergeSort {
    public static void merge(int arr[], int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int L[] = new int[n1];
        int R[] = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[left + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[mid + 1 + j];

        int i = 0, j = 0, k = left;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j])
                arr[k++] = L[i++];
            else
                arr[k++] = R[j++];
        }
        while (i < n1)
            arr[k++] = L[i++];
        while (j < n2)
            arr[k++] = R[j++];
    }

    public static void sort(int arr[], int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;
            sort(arr, left, mid);
            sort(arr, mid + 1, right);
            merge(arr, left, mid, right);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        int arr[] = new int[n];
        System.out.println("Enter the elements:");
        for (int i = 0; i < n; i++)
            arr[i] = sc.nextInt();
        sort(arr, 0, n - 1);
        System.out.println("Sorted array: " + Arrays.toString(arr));
        sc.close();
    }
}
```
## OUTPUT
<img width="940" height="145" alt="image" src="https://github.com/user-attachments/assets/0b994f37-8350-4b21-9b9d-f17f695ac98e" />

## RESULT
The program has been successfully implemented and executed.

