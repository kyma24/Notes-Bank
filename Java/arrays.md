```java
class Main {
  public static void main(String[] args) {

		int[ ] arr;
		//defines data type of array and the name
		int[ ] arr = new int[5];
		//declares array of 5 integers. "new" allocates new space in memory for the values of array
		arr[2] = 42;
		//assigning value 42 to 2 as index

		//initializing arrays
		//telling machine what type of array it is: reserve certain memory space to store info: when initializing, machine grabs spaces to put the values into
		String[ ] myNames = { "A", "B", "C", "D"};
		System.out.prinln(myNames[2]);
		//array literal: placing comma-separated values into curly brackets(defines the elements of the array, only used if you already know the values)

		String[] days = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
	  for (int i = 0; i < days.length; i++) //use .length to define the number of elements in the array
		{
			System.out.println(days[i]);
	  }
	// length is essentially a variable: if it were a method, it would need to have parentheses

		int [ ] myArr = {6, 42, 3, 7};
		int sum = 0;
		for(int x = 0; x < myArr.length; x++)
		{
			sum += myArr[x];
		}
		System.out.println(sum);
		//output >> 58

//enhanced for loop: easier to type, a little harder to read(same as above myArr array)
		int[ ] numbers = {6, 42, 3, 7};
		int sum = 0;
		for (int i: numbers)
		{
			sum += i;
			//variable established within for loop parentheses shall only be used inside the for loop: for each iteration of loop, variable will be equal to corresponding element in array: lets for loop access elements of array
		}
		System.out.println(sum);

		//multidimensional array: array that contains other arrays.
		int[ ][ ] sample = { {1, 2, 3}, {4, 5, 6} };
		//declares array w/ two arrays as elements. two indexes are row index & column index
		int x = sample[1][0];
		System.out.println(x);
		//stack two indexes together: (0,0) is first. first bracket is index for row number: 0 is the first nested array, for example; second is for column. 2D indexes are most common multidimensional array

		int[ ][ ] myArr = { {1, 2, 3}, {4}, {5, 6, 7} };
		myArr[0][2] = 42;
		int x = myArr[1][0]; //4
		//above contains 3 arrays
		//can nest as many arrays as needed
  }
}
```