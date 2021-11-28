```java
/*tests variable for equality against a list of values
each value is called a case
variable being switched on is checked for each case
*/
int day = 4
switch (day % 7) {
		//^ loops it and finds the day
	  case 0 :
     System.out.println("Sunday");
     break; //optional
   
		case 1 :
     System.out.println("Monday");
     break; //optional
		
		case 2 :
			System.out.println("Tueday");
			break;
		
		case 3:
			System.out.println("Wednesday");
			break;

		case 4:
			System.out.println("Thursday");
			break;

		case 5:
			System.out.println("Friday");
			break;

		case 6:
			System.out.println("Saturday");
			break;

	  default :
     System.out.println("Error");
			break;

//You can have any number of case statements.
//When the variable being switched on is equal to a case, the statements following that case will execute until a break statement is reached.
//When a break statement is reached, the switch terminates, and the flow of control jumps to the next line after the switch statement.
//Not every case needs to contain a break. If no break appears, the flow of control will fall through to subsequent cases until a break is reached.
}

int Day = 3;
switch(Day)
{
	case 6:
		System.out.println("Saturday");
		break;
	case 7:
		System.out.println("Sunday");
		break;
	default:
		System.out.println("Weekday");
	//always last statement in switch: does not need break, since it ends the switch: executes when none of the statements are satisfied
}

```
