#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to encrypt the text
void encryptText() {
    char plain[100], key[100];
    int i, j;

    printf("\nEnter the plain text (A-Z only): ");
    scanf("%s", plain);

    printf("Enter the key (A-Z only): ");
    scanf("%s", key);

    printf("Encrypted Text: ");
    for (i = 0, j = 0; i < strlen(plain); i++) {
        // Reset key index if it ends
        if (j == strlen(key))
            j = 0;

        // Convert characters to uppercase and shift
        char p = toupper(plain[i]) - 'A';
        char k = toupper(key[j]) - 'A';
        char encrypted = (p + k) % 26 + 'A';

        printf("%c", encrypted);
        j++;
    }
    printf("\n");
}

// Function to decrypt the text
void decryptText() {
    char cipher[100], key[100];
    int i, j;

    printf("\nEnter the encrypted text (A-Z only): ");
    scanf("%s", cipher);

    printf("Enter the key (A-Z only): ");
    scanf("%s", key);

    printf("Decrypted Text: ");
    for (i = 0, j = 0; i < strlen(cipher); i++) {
        if (j == strlen(key))
            j = 0;

        char c = toupper(cipher[i]) - 'A';
        char k = toupper(key[j]) - 'A';
        char decrypted = (c - k + 26) % 26 + 'A';

        printf("%c", decrypted);
        j++;
    }
    printf("\n");
}

// Main menu
int main() {
    int choice;



    while (1) {
        printf("\n--- Vigenère Cipher ---\n");
        printf("1. Encrypt Text\n");
        printf("2. Decrypt Text\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 1) {
            encryptText();
        } else if (choice == 2) {
            decryptText();
        } else if (choice == 3) {
            printf("Exiting program.\n");
            break;
        } else {
            printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
}
