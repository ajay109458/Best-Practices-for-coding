# Best Codinng Practice in Java

Standard conventions in java to write best and bug free code.

## Unit objectives

* Follow best practices for class sizes, method sizes, and method names
* Understand the importance of refactoring
* Gain consistency in coding style and use of comments
* Use built-in logging

### Prefer returning Empty Collections instead of Null

If a program is returning a collection which does not have any value, make sure an Empty collection is returned rather than Null elements. This saves a lot of “if else” testing on Null Elements.

```
public class getLocationName {
	return (null==cityName ? "": cityName);
}
```

### Use Strings carefully

If two Strings are concatenated using “+” operator in a “for” loop, then it creates a new String Object, every time. This causes wastage of memory and increases performance time. Also, while instantiating a String Object, constructors should be avoided and instantiation should happen directly. For example:

```
//Slower Instantiation
String bad = new String("Yet another string object");

//Faster Instantiation
String good = "Yet another string object"
```

### Avoid unnecessary Objects

One of the most expensive operations (in terms of Memory Utilization) in Java is Object Creation. Thus it is recommended that Objects should only be created or initialized if necessary.

### Dilemma between Array and ArrayList

Developers often find it difficult to decide if they should go for Array type data structure of ArrayList type. They both have their strengths and weaknesses. The choice really depends on the requirements.

```
import java.util.ArrayList;

public class arrayVsArrayList {

	public static void main(String[] args) {
		int[] myArray = new int[6];
		myArray[7]= 10; // ArraysOutOfBoundException

		//Declaration of ArrayList. Add and Remove of elements is easy.
		ArrayList<Integer> myArrayList = new ArrayList<>();
		myArrayList.add(1);
		myArrayList.add(2);
		myArrayList.add(3);
		myArrayList.add(4);
		myArrayList.add(5);
		myArrayList.remove(0);

		for(int i = 0; i < myArrayList.size(); i++) {
		System.out.println("Element: " + myArrayList.get(i));
		}

		//Multi-dimensional Array
		int[][][] multiArray = new int [3][3][3];
	}
}
```

* Arrays have fixed size but ArrayLists have variable sizes. Since the size of Array is fixed, the     memory gets allocated at the time of declaration of Array type variable. Hence, Arrays are very fast. On the other hand, if we are not aware of the size of the data, then ArrayList is More data will lead to ArrayOutOfBoundException and less data will cause wastage of storage space.
* It is much easier to Add or Remove elements from ArrayList than Array
* Array can be multi-dimensional but ArrayList can be only one dimension.

### Check Oddity

Have a look at the lines of code below and determine if they can be used to precisely identify if a given number is Odd?

```
public boolean oddOrNot(int num) {
	return num % 2 == 1;
}
```

Have a look at the lines of code below and determine if they can be used to precisely identify if a given number is Odd?

```
public boolean oddOrNot(int num) {
	return num % 2 == 1;
}
```
These lines seem correct but they will return incorrect results one of every four times (Statistically speaking). Consider a negative Odd number, the remainder of division with 2 will not be 1. So, the returned result will be false which is incorrect!

This can be fixed as follows:
```
public boolean oddOrNot(int num) {
	return (num & 1) == 1;
}
```

## Difference between single quotes and double quotes

```
public class Haha {
	public static void main(String args[]) {
	System.out.print("H" + "a");
	System.out.print('H' + 'a');
	}
}
```

From the code, it would seem return “HaHa” is returned, but it actually returns Ha169. The reason is that if double quotes are used, the characters are treated as a string but in case of single quotes, the char -valued operands ( ‘H’ and ‘a’ ) to int values through a process known as widening primitive conversion. After integer conversion, the numbers are added and return 169.

## Avoiding Memory leaks by simple tricks

Memory leaks often cause performance degradation of software. Since, Java manages memory automatically, the developers do not have much control. But there are still some standard practices which can be used to protect from memory leakages.

* Always release database connections when querying is complete.
* Try to use Finally block as often possible.
* Release instances stored in Static Tables.

## How to handle Null Pointer Exceptions

Null Pointer Exceptions are quite common in Java. This exception occurs when we try to call a method on a Null Object Reference. For example,

```
int noOfStudents = school.listStudents().count;
```

If in the above example, if get a NullPointerException, then either school is null or listStudents() is Null. It’s a good idea to check Nulls early so that they can be eliminated.

```
private int getListOfStudents(File[] files) {
	  if (files == null)
	    throw new NullPointerException("File list cannot be null");
	}
```
