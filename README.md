# Find-the-Armstrong-Numbers-in-a-Given-Range-in-C

Find the Armstrong Numbers in a Given Range in C
Given two integer inputs as the intervals. The objective is to find all the Armstrong numbers in a given range. We therefore write a code to Find the Armstrong Numbers in a Given Range in C.

Example
Input : 10 10000
Output : 153 370 371 407 1634 8208 9474
Find the Armstrong Numbers in a Given Range in C
Write a C Program to display the Armstrong Numbers in between the given range
Working
An Armstrong number or a Narcissistic number is any number that sums up to itself when each of its digits is raised to the power of total number of digits in the number. Let us try to understand this through the below example,

abcd… = an + bn + cn + dn + …
Where n is the order(length/digits in number)
Let’s look at some examples of Armstrong Numbers.

Examples
Here are few examples that’ll help you to understand the concept better.

Find the Armstrong Number in a Given Range in C
Example 1
Number = 370 (order = 3)
370 = 3^3 + 7^3 + 0^3
= 27 + 343 + 0
= 370
Example 2
Example = 1634 (order = 4)
1634 = 1^4 + 6^4 + 3^4 + 4^4
= 1 + 1296 + 81 + 256
= 1634
As you can see in both the above examples the numbers 370 and 1634 are the sum of their digits raised to the power of total number of digits i.e; 3 and 4 respectively. These kind of numbers are known as armstrong numbers. Some more examples of armstrong numbers are 0, 1, 153,  371 and 407

While loop in C
C Code
Run

// Write a C Program to display the Armstrong numbers in between the given range
#include<stdio.h>
#include<math.h>
using namespace std;
// number of digits in a number is order
int order(int x)
{
    int len = 0;
    while (x)
    {
        len++;
        x = x/10;
    }
    return len;
}

void armstrong(int low, int high){
    
    for(int num = low; num <= high; num++){
        
        int sum = 0, temp, digit, len;
        temp = num;
        
        // function to get order(length)
        len = order(num);
        
        // loop to extract digit, find powers & add to sum
        while(temp != 0)
        {
            // extract digit
            digit = temp % 10;

            // add power to sum
            sum = sum + pow(digit,len);;
            temp /= 10;
        };
    
        if(sum == num)
            printf("%d ",num);
    }
}

// Driver Code
int main ()
{
    int low, high;
 
    printf("Enter a lower & upper bounds: ");
    scanf("%d %d",&low,&high);
 
    // get armstrong numbers
    armstrong(low, high);
}
Output
Enter a lower & upper bounds: 10 10000
153 370 371 407 1634 8208 9474 
Method 2
Method 2 uses recursion in C
Run
#include<stdio.h>
#include<math.h>

// number of digits in a number is order
int order(int x)
{
    int len = 0;
    while (x)
    {
        len++;
        x = x/10;
    }
    return len;
}

int getArmstrongSum(int num, int order){
    
    if(num == 0)
        return 0;
    
    int digit = num % 10;
    
    return pow(digit, order) + getArmstrongSum(num/10, order);
}

void armstrong(int low, int high){
    
    for(int num = low; num <= high; num++){
        
        int sum = 0, temp, digit, len;
        temp = num;
        
        // function to get order(length)
        len = order(num);
    
        if(num == getArmstrongSum(num, len))
            printf("%d ",num);
    }
}


// Driver Code
int main ()
{
    int low, high;
 
    printf("Enter a lower & upper bounds: ");
    scanf("%d %d",&low,&high);
 
    // get armstrong numbers
    armstrong(low, high);
}
Output
Enter a lower & upper bounds: 1 1000
1 2 3 4 5 6 7 8 9 153 370 371 407
