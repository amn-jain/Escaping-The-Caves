# Substitution cipher

## Commands

Commands to reach the first ciphertext in the game.

> climb => read => enter => read 

## Analysis

We started with assuming that it is a Caesar Cipher and check for all 26 possible output. But after checking that we didn’t find any useful result. So we switched to substitution cipher. Also while reading the ciphertext we find out that there are capital letters in between words and location of “.” is also wrong. This also helps us to know that letters are shifted. We use this info to correct the position of the word. After that, we use frequency analysis to proceed.

## Maping

> Ciphertext space = ['0', '3', '8', 'a', 'b', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'm', 'n', 'o', 'p', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y']

> Plaintext space = ['4', '6', '9', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'y']

In the deciphered text we got to know that the digits are shifted by 8, so 8 itself must be shifted by some number x, so (2 * x) must be 8, so x = 4. The digits are shifted by 4 towards the left, so 0 maps to 6 and 3 maps to 9.

The mapping between the elements of ciphertext space and the elements of plaintext space:

> 'y' => 'e', 'm' => 't', 'e' => 'h', 'a' => 's', 'w' => 'i', 's' => 'r', 't' => 'f', 'h' => 'n', 'u' => 'd', 
'g' => 'o', 'r' => 'g', 'j' => 'm', 'p' => 'a', 'n' => 'u', 'i' => 'c', 'o' => 'b', 'f' => 'p', 'v' => 'w', 
'd' => 'q', 'x' => 'y', 'k' => 'l', 'b' => 'v', ‘8’ => ‘4’, ‘0’ => ‘6’, ‘3’ => ‘9’ 

## Password

Final command to clear this level is "tyRgU69diqq".