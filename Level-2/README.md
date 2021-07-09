# Playfair Cipher

## Commands

Commands to reach the ciphertext in the game.

> go => back => read 

## Analysis

We have been informed that there are some funny patterns on the distant boulder so after entering ‘go’ command to reach that boulder we landed on a page where we are given a morse code (... . -.-. ..- .-. .. - -.--) which on decryption yields a key => ‘SECURITY’. The paragraph next to this morse code has ‘PLAY FAIR’ capitalized which intuitively gives us the name of the cryptosystem which may have been used to encrypt the text. We did not find anything else so we headed back to the main chamber using ‘back’ command. There we found a glass panel so by using ‘read’ we found the Cipher Text.

## Decryption Algorithm

Algorithm used is PlayFair, in this we have a key and message. To encode the message we create a matrix of size 5x5 and filled it with different alphabet (‘J’ is put in same cell as ‘I’), We firstly put the key in the matrix and filled the rest of matrix with remaining alphabet (in increasing order). 
Now to decode we select pairs of alphabet and find the location of those alphabet in the matrix. There are three possible location of these two alphabet :
Both are in a row : Then replace them by the alphabet which is on their left.
Both are in column : Then replace them by the alphabet which is on their top.
Else :  Use those alphabet to create a rectangle and replace them by the other two corners of the rectangle. (for any alphabet replace it with that corner alphabet which has same row)
After decrypting the message we remove the extra ‘X’ which was placed to separate the same alphabet. And also replace some ‘I’ with ‘J’ (as both allotted the same cell)

Final Plain Text :
BE WARY OF THE NEXT CHAMBER, THERE IS VERY LITTLE JOY THERE. SPEAK OUT THE PASSWORD "OPEN_SESAME" TO GO THROUGH. MAY YOU HAVE THE STRENGTH FOR THE NEXT CHAMBER. TO FIND THE EXIT YOU FIRST WILL NEED TO UTTER MAGIC WORDS THERE.

## Password

Final command to clear this level is "OPEN_SESAME".