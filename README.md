# EX. NO: 1(A) : IMPLEMENTATION OF CAESAR CIPHER

## AIM:
To implement the simple substitution technique named Caesar cipher using C language.

## ALOGORITHM:

STEP-1: Read the plain text from the user.

STEP-2: Read the key value from the user.

STEP-3: If the key is positive then encrypt the text by adding the key with each character in the plain text.

STEP-4: Else subtract the key from the plain text.

STEP-5: Display the cipher text obtained above.

## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

/* Shift every letter by 'key' (positive = encrypt, negative = decrypt) */
void caesar(char text[], int key)
{
    int i;
    key = ((key % 26) + 26) % 26;          /* normalise key to 0..25 */

    for (i = 0; text[i] != '\0'; i++)
    {
        if (isupper(text[i]))
            text[i] = (text[i] - 'A' + key) % 26 + 'A';
        else if (islower(text[i]))
            text[i] = (text[i] - 'a' + key) % 26 + 'a';
        /* non-letters are left unchanged */
    }
}

int main()
{
    char plain[200], text[200];
    int key;

    printf("Enter the plain text: ");
    fgets(plain, sizeof(plain), stdin);
    plain[strcspn(plain, "\n")] = '\0';     /* remove trailing newline */

    printf("Enter the key value: ");
    scanf("%d", &key);

    /* Encryption */
    strcpy(text, plain);
    caesar(text, key);                      /* add key */
    printf("\nPlain text      : %s\n", plain);
    printf("Encrypted text  : %s\n", text);

    /* Decryption */
    caesar(text, -key);                     /* subtract key */
    printf("Decrypted text  : %s\n", text);

    return 0;
}
```


## OUTPUT:
<img width="715" height="471" alt="Screenshot 2026-10-23 143341" src="https://github.com/user-attachments/assets/60b19277-e0bb-4340-8fac-5b80ce0d5966" />


## RESULT :
 Thus the implementation of ceasar cipher had been executed successfully.
