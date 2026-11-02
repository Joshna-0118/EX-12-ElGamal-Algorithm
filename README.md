# EX-12-ElGamal-Algorithm
Implementation of the ElGamal Encryption and Decryption Algorithm in C using public-key cryptography, modular exponentiation, and modular inverse operations.

## Name: Joshna.M
## Reference Number: 212225230118

# AIM:
To Implement ELGAMAL ALGORITHM

# ALGORITHM:

    1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

    2. Initialization:
        Select a large prime ( p ) and a primitive root ( g ) modulo ( p ) (these are public values).
        The receiver chooses a private key ( x ) (a random integer), and computes the corresponding public key ( y = g^x \mod p ).

    3. Key Generation:
        The public key is ( (p, g, y) ), and the private key is ( x ).

    4. Encryption:
        The sender picks a random integer ( k ), computes ( c_1 = g^k \mod p ), and ( c_2 = m \times y^k \mod p ), where ( m ) is the message.
        The ciphertext is the pair ( (c_1, c_2) ).

    5. Decryption:
        The receiver computes ( s = c_1^x \mod p ), and then calculates the plaintext message ( m = c_2 \times s^{-1} \mod p ), where ( s^{-1} ) is the modular inverse of ( s ).

    6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

# PROGRAM:
```
#include <stdio.h>

int power(int a, int b, int p) {
    int result = 1;
    for (int i = 0; i < b; i++)
        result = (result * a) % p;
    return result;
}

int inverse(int a, int p) {
    for (int i = 1; i < p; i++)
        if ((a * i) % p == 1)
            return i;
    return -1;
}

int main() {
    int p, g, x, k, m;
    int y, c1, c2, s, decrypted;
    printf("Enter prime number: ");
    scanf("%d", &p);
    printf("Enter primitive root: ");
    scanf("%d", &g);
    printf("Enter private key: ");
    scanf("%d", &x);
    printf("Enter message: ");
    scanf("%d", &m);
    printf("Enter random key: ");
    scanf("%d", &k);
    y = power(g, x, p);
    c1 = power(g, k, p);
    c2 = (m * power(y, k, p)) % p;
    s = power(c1, x, p);
    decrypted = (c2 * inverse(s, p)) % p;
    printf("\nPublic Key: (%d, %d, %d)", p, g, y);
    printf("\nCiphertext: (%d, %d)", c1, c2);
    printf("\nDecrypted Message: %d\n", decrypted);

    return 0;
}
```

# OUTPUT:

<img width="1019" height="306" alt="image" src="https://github.com/user-attachments/assets/75a0c417-c1fc-4a21-9b79-35c36d217e57" />

# RESULT:
The ElGamal Encryption and Decryption Algorithm was successfully implemented in C. The program generated public and private keys, encrypted the given message into ciphertext, and successfully decrypted it to retrieve the original message.
