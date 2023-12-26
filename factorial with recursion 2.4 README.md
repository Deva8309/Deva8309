y deva harsha
192311126
#include <stdio.h>
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

int main() {
    int number;
    printf("Enter a non-negative integer: ");
    scanf("%d", &number);
    if (number < 0) {
        printf("Please enter a non-negative integer.\n");
    } else {
        printf("Factorial of %d = %d\n", number, factorial(number));
    }

    return 0;
}

C:\Users\devah\Pictures\Screenshots\Screenshot 2023-12-26 190828.png
