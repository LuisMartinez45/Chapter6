# Chapter6
exercises chapter 6
## 6.1
```c
#include <stdio.h>
#include <math.h>

char line[100];            
float distance;             
float square;               
float square_root;          

int main() {
	printf("Enter the distance: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%f", &distance);

	square = distance * distance;
	printf("Square of distance is %f\n", square);

	square_root = sqrtf(square);
	printf("Square root of previous result is %f\n", square_root);

	return(0);
}
```
## 6.2
```c
#include <stdio.h>

float percent_right;    
char grade;             
char line[100];         

int main() {
	printf("Enter the percentage correct: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%f", &percent_right);

	if (percent_right >= 91.0) {
		grade = 'A';
	} else if (percent_right >= 81.0) {
		grade = 'B';
	} else if (percent_right >= 71.0) {
		grade = 'C';
	} else if (percent_right >= 61.0) {
		grade = 'D';
	} else {
		grade = 'F';
	}

	printf("The grade is %c\n", grade);

	return(0);
}
```
## 6.3
```c
#include <stdio.h>

int percent_right;      
char grade;             
char modifier;          
char line[100];         

int main() {
	printf("Enter the percentage correct: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%d", &percent_right);

	modifier = ' ';   /* empty space by default (no modifier) */

	if (percent_right > 100) {
		printf("Error: out of bounds\n");
		return(1);
	} else if (percent_right < 0) {
		printf("Error: out of bounds\n");
		return(1);
	} else if (percent_right >= 91) {
		grade = 'A';
		if (percent_right >= 98) {
			modifier = '+';
		} else if (percent_right <= 93) {
			modifier = '-';
		}
	} else if (percent_right >= 81) {
		grade = 'B';
		if (percent_right >= 88) {
			modifier = '+';
		} else if (percent_right <= 83) {
			modifier = '-';
		}
	} else if (percent_right >= 71) {
		grade = 'C';
		if (percent_right >= 78) {
			modifier = '+';
		} else if (percent_right <= 73) {
			modifier = '-';
		}
	} else if (percent_right >= 61) {
		grade = 'D';
		if (percent_right >= 68) {
			modifier = '+';
		} else if (percent_right <= 63) {
			modifier = '-';
		}
	} else {
		grade = 'F';
	}

	printf("The grade is %c%c\n", grade, modifier);

	return(0);
}
```
## 6.4
```c
#include <stdio.h>

char line[100];            
int cents;                  
int quarters = 0;          
int dimes = 0;             
int nickels = 0;            
int pennies = 0;           

int main() {
	printf("Enter the number of cents we have: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%d", &cents);

	if (cents > 99) {
		printf("Error: has to be less than $1.00\n");
		return(1);
	} else if (cents < 1) {
		printf("Error: can not be less than a penny\n");
		return(1);
	}

	while (1) {
		if (cents >= 25) {
			++quarters;
			cents -= 25;
		} else if (cents >= 10) {
			++dimes;
			cents -= 10;
		} else if (cents >= 5) {
			++nickels;
			cents -= 5;
		} else if (cents >= 1) {
			++pennies;
			--cents;
		} else if (cents == 0) {
			break;
		}
	}

	printf("%d quarters %d dimes %d nickels %d pennies\n",
		quarters, dimes, nickels, pennies);

	return(0);
}
```
## 6.5
```c
#include <stdio.h>

char line[100];             
int year;                  
int leap_year = 0;          

int main() {
	printf("Enter a year: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%d", &year);

	
	if (year % 4 == 0) {
		leap_year = 1;

		
		if (year % 100 == 0) {
			if (year % 400 != 0) {
				leap_year = 0;
			}
		}

	}

	if (leap_year == 1) {
		printf("%d is a leap year.\n", year);
	} else {
		printf("%d is not a leap year.\n", year);
	}

	return(0);
}
```
## 6.6
```c
#include <stdio.h>

char line[100];             
float hours;                
float wage;                 
float overtime = 0.0;      
float paycheck;            

int main() {
	printf("Enter hours worked: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%f", &hours);

	printf("Enter wage: ");
	fgets(line, sizeof(line), stdin);
	sscanf(line, "%f", &wage);

	if (hours > 40.0) {
		overtime = (hours - 40.0) * 1.5;
		hours = 40.0;
		paycheck = (hours * wage) + (overtime * wage);
	} else {
		paycheck = hours * wage;
	}

	printf("Paycheck: $%0.2f\n", paycheck);

	return(0);
}
```
