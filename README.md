# EX-10-Diffee-Hellman

## AIM:
To implement the Diffie-Hellman algorithm to securely exchange keys and generate a shared secret key.

## DESIGN STEPS:
Step 1:
Design the Diffie-Hellman key exchange algorithm.

Step 2:
Implement the algorithm using C.

Step 3:
The Diffie-Hellman algorithm uses a large prime number p and a primitive root g. Both Alice and Bob select private keys and exchange public keys computed using the formula:
```
Public Key = (g^Private Key) % p
```
After exchanging public keys, both compute a shared secret key using:
```
Shared Secret = (Other's Public Key^Private Key) % p
```
## PROGRAM:
```c
#include <stdio.h>
#include <math.h>
int modExp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    int p;  
    int g;   
    printf("Enter a prime number (p): ");
    scanf("%d", &p);
    printf("Enter a base (g): ");
    scanf("%d", &g);
    int a, b;
    printf("Enter levi private key: ");
    scanf("%d", &a);
    printf("Enter armin private key: ");
    scanf("%d", &b);
 
    int A = modExp(g, a, p); 
    int B = modExp(g, b, p);  
    
    printf("levi Public Key: %d\n", A);
    printf("armin Public Key: %d\n", B);
    int sharedKeylevi = modExp(B, a, p);  
    int sharedKeyarmin = modExp(A, b, p);    
    
    printf("Shared Secret Key (levi): %d\n", sharedKeylevi);
    printf("Shared Secret Key (armin): %d\n", sharedKeyarmin);

    if (sharedKeylevi == sharedKeyarmin) {
        printf("Key Exchange Successful! Shared Secret Key: %d\n", sharedKeylevi);
    } else {
        printf("Key Exchange Failed!\n");
    }

    return 0;
}

```
## OUTPUT:
![image](https://github.com/user-attachments/assets/2b799853-320c-4bdb-8ac2-c1309d62d9d5)



## RESULT:
The program for the Diffie-Hellman algorithm is executed successfully, and Alice and Bob have securely derived a shared secret key.
