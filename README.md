# Array_Homework7
/*
Jose Baca
March 30, 2019
Homework 7 - COP2220
*/
#define _CRT_SECURE_NO_WARNINGS // used to all scanf to work
#include <stdio.h>  // used for printf and scanf functions

// function prototypes go here
void displayArray(int a[], int length); // do not change this line
int countEvenPositive(int a1[], int length);
void addArrays(int a1[], int a2[], int a3[], int length);
void reverseArray(int a1[], int length);
void initializeWordString(char base[], char word[]);
int countLetters(char a1[]);
int searchString(char a1[], char letterToSearch);

int main()
{
	printf("Homework 7 by Jose Baca\n");

	// demonstrate the use of countEvenPositive() by using an array that contains 2,1,-5,0,8,-8
	// of length 6. Display the array contents and show the result of countEvenPositive()
	int test1[] = { 2, 1, -5, 0, 8, -8 };
	printf("The array contains ");
	displayArray(test1, 6);
	printf("\nThe number of even positive integers is %d\n", countEvenPositive(test1, 6));

	// demonstrate the use of addArrays using the array 1,2,3,4  and  4,6,8,10 of length 4.
	// Display the added array which should be 5, 8, 11, 14
	int test2[] = { 1, 2, 3, 4 };
	int test3[] = { 4, 6, 8, 10 };
	int test4[4];
	addArrays(test2, test3, test4, 4);
	printf("\nThe two array sums are ");
	displayArray(test4, 4);
	printf("\n");

	// demonstrate the use of reverseArray using the array 1,2,3,4 of length 4.
	// Display the reversed array.
	reverseArray(test2, 4);
	printf("\nThe reversed array is ");
	displayArray(test2, 4);
	printf("\n");

	// demonstrate the use of countLetters using the array "Aa123Mm@#$Zz".
	// Display the count
	char c1[] = "Aa123Mm@#$Zz";
	printf("\nThe number letters in %s is %d\n", c1, countLetters(c1));

	// demonstrate the use of initializeWordString using the array "happy".
	// the word array should be 6 characters long. Display the word array.
	char c2[] = "happy";
	char c3[6];
	initializeWordString(c2, c3);
	//printf("\nThe new string is %s\n ", c3);

	// demonstrate the use of searchString using the array "happy" and search
	// for the character 'a'. Then perform the same test with character 'e'
	printf("\nThe result of the letter %c in the array %s is %d", 'a', c2, searchString(c2, 'a'));
	printf("\nThe result of the letter %c in the array %s is %d", 'e', c2, searchString(c2, 'e'));
	printf("\n");

	return 0;
}
// The function countEvenPositive() has 2 input parameters.
// 1) input parameter a1 is an integer array
// 2) input parameter length is the length of the a1 array
// The function countEvenPositive() returns an integer value.
// The function countEvenPositive() will count the number of even positive numbers
// that exist in the integer array[]. The count will start from index 0 to index
// length - 1. Assume 0 is a positive and even number.
// Example: a1 array contains: 2,1,-5,0,8,-8 and the length is 6. The returned
// value will be 3 (2, 0, and 8). If the length is <= 0 then return 0.
int countEvenPositive(int a1[], int length)
{
	int count = 0;
	for (int i = 0; i < length; i++) {
		if ((a1[i] % 2 == 0)&&(a1[i]>=0)) {
			count++;
		}
	}
	count = count + 1;
	return count;
}

// The function addArrays() has 4 input paramters. The input parameters are
// 1) input parameter a1 is an integer array
// 2) input parameter a2 is an integer array
// 3) input parameter a3 is an integer array
// 4) input parameter length is the length of each array. 
// Assume arrays a1, a2, and a3 are the same length
// The function addArrays() does not return a value (void).
// The function addArrays() will add the elements of a1 and a2 and put the result
// in a3. The addition is performed element by element. Example:
// the length is 4.
// a1 contains the following elements:  1, 4, 5, 2
// a2 contains the following elements:  0, 2, 7, -4
// after the function a3 should contain: 1, 6, 12, -2
void addArrays(int a1[], int a2[], int a3[], int length)
{
	int i;
	for (i = 0; i < length; i++) {
		a3[i] = 0;
	}

	for (i = 0; i < length; i++) {
		a3[i] = a1[i] + a2[i] + a3[i];
	}
}

// The function reverseArray() has 2 input parameters.
// 1) input parameter a1 is an integer array
// 2) input parameter length is the length of the a1 array
// The function reverseArray() does not return a value (void)
// The content of the array is to be reversed. Example1:
// a1 array contains 1,2,3,4 before the function with length equal to 4.
// After the function array a1 contains 4,3,2,1.
// Example2: a1 array contains 1,2,3,4,5 before the function with length equal to 5.
// After the function array a1 contains 5,4,3,2,1.
void reverseArray(int a1[], int length)
{
	int i, swap;
	i = length / 2;
	for (int j = 0; j < i; j++) {
		swap = a1[j];
		a1[j] = a1[length - 1 - j];
		a1[length - 1 - j] = swap;
	}
}

// The function countLetters() has 1 input parameter.
// 1) input parameter a1 is a character array that is null terminated
// The function countLetters() returns an integer value.
// The countLetters() function will count the number of small letters from a to z
// and capital letter from A to Z in the a1 array. The count will be
// the returned value of the countLetters() function.
// Example: The a1 array contains "a2!&@AZx96dfg"
// The countLetters() function will return the value of 7.
int countLetters(char a1[])
{
	int i;
	int count;
	count = 0;
	for (i = 0; a1[i] <= '\0'; i++) {
		if ((a1[i]>='a') && (a1[i]<='z'))
		{
			count++;
		}
		else if ((a1[i] >= 'A') && (a1[i] <= 'Z')) {
			count++;
		}
	}
	return count;
}

// The function initializeWordString() has 2 input parameter2.
// 1) input parameter base is a character array that is null terminated
// 2) input parameter word is a character array that is null terminated
// initializeWordString() function will count the number of characters in the
// base character array which is null terminated. The null terminator does not count
// as a character. The function will insert the dash character ('-') in the word character 
// array such that the base and word arrays are the same length. Assume the capacity
// of the word array is large enough to support the dash characters needed.
// Example: base array contains "happy". The result of the word array should be "-----"
// (five dashes) and then null terminated. 
void initializeWordString(char base[], char word[])
{
	int count=0;
	int i,j;
	for (i = 0; base[i] <= '\0'; i++) {
		count++;
	}
	j = count;
	for (i = 0; i < count; i++) {
		word[i] = '-';
	}
	word[j] = '\0';

}

// The function searchString() has 2 input parameter.
// 1) input parameter a1 is a character array that is null terminated
// 2) input parameter letterToSearch is a character type
// The function searchString() returns an integer value.
// The function searchString() will search the a1 array for the occurrence
// of the letterToSearch. If letterToSearch is contained at least 1 time in the 
// array then the searchString() function will return a 1, otherwise searchString()
// will return a 0.
// Example: a1 array contains abcdef and the letterToSearch is c, then a 1 is returned.
// Example: a1 array contains abcdef and the letterToSearch is m, then a 0 is returned.
int searchString(char a1[], char letterToSearch)
{
	int i, count;
	count = 0;
	for (i = 0; a1[i] <= '\0'; i++) {
		if (a1[i] == letterToSearch) {
			count++;
		}
	}
	return count;
}

// do not change this function
// The function displayArray() displays the contents of the array
// word character array a lower case letter. The word character array is
// null terminated.
void displayArray(int a[], int length)
{
	for (int i = 0; i < length; i++)
	{
		printf("%d ", a[i]);
	}
}


