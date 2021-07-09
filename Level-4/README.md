# 6 Round DES

## Commands

Commands to reach the ciphertext in the game.

> go -> dive -> dive -> back -> dive-> pull -> back -> back -> go -> wave  After this we broke the connection and then connected again to level 4.  Then we used the following command:- read-> password

## Analysis

It was given that 2 letters were stored in 1 byte. So we tried to form all possible pairs of letters and search for some pattern but couldn’t find any. After trying a lot of inputs we saw that the output only has some limited letters i.e. from ‘f’ to ‘u’. These are a total of 16 letters which can be coded in 4 bits (‘f’: ‘0000’, ‘g’: ‘0001’, ‘h’: ‘0010’, ‘i’: ‘0011’, ‘j’: ‘0100’, ‘k’: ‘0101’, ‘l’: ‘0110’, ‘m’: ‘0111’, ‘n’: ‘1000’, ‘o’: ‘1001’, ‘p’: ‘1010’, ‘q’: ‘1011’, ‘r’: ‘1100’, ‘s’: ‘1101’, ‘t’: ‘1110’, ‘u’: ‘1111’). Now we are able to store 2 letters in 1 byte (8 bits). We restricted our input according to output (i.e. from ‘f’ to ‘u’).  

It was given that the system is either 4 or 6 rounds. As it was written that 4 rounds DES is easy to break, so we started with 6 rounds. As we know that for r rounds we need r-2 round characteristics. So for 6 rounds we need 4 round characteristics. So we used some part of 5 round characteristics (405C0000, 04000000, 1/4, 04000000, 00540000, 5/128, 00540000, 00000000, 1, 00000000, 00540000, 5/128, 00540000, 04000000) (Given in lecture 7 page 12). Next we need to know how many input and output pairs are required, which we calculated using the 20/p formulae. (Given in lecture 7 slide 11). It came around 50k. So we used 1 lakh input and output pairs for assurance. The XOR between the L0, L0′ is equal to ‘405C0000’ and R0, R0′ is ‘04000000’ and by taking the inverse from the initial permutation we find input pairs. From these input pairs we generate output pairs by connecting to SSH server using ‘paramiko’ library in python.

We used the method of differential cryptanalysis given in lecture 7 slide 11. This generates the frequency of all 8 subkeys of key 6. From that we see that 6 of the 8 subkeys have large differences (approx 500 or more) in their top and the 2nd best value whereas in 2 of the subkeys (generated from S3, S4 boxes) there is only a 50 - 100 difference. So from this we conclude that we got 6 subkeys. 

Now as we know all the keys are of length 48 and these are generated from a master key of 56 bit. We copied the function(set_the_key) given in des.txt file to see which bit goes to which position in key 6. Since we know 6 subkeys of key 6 (i.e. 36 bits out of 48 bits), we know 36 bits out of 56 in master key. Now total 20 bits are unknown. And it generates 220 possible master keys. We stored all possible masterkeys and brute force through all values. This give a master key and by using this we generate all 6 keys and decrypt the password (‘fhsrnrgrrogfjsrliqmohkfhsjjmortt’) and we got decipher text (‘mjlpmmmolplmljmflpmmifififififif’). Now we tried this but it didn’t work. Since it was our assumption that input only belongs from letter ‘f’ to ‘u’, so it might not work. So we convert it into bits and use ASCII values, and we get tjwyjgdpjw000000. Then we removed extra zeros (we think 0’s were just for padding) from the end and it worked. 

Final Keys Obtained: 

Key 1 '111111000100111110000111111111011101011010000001'
Key 2 '011011110011111101100010001010111011101000111100'
Key 3 '111010101111110011101101011100010101110110110110'
Key 4 '110110011110011101011010000011010000100010111111'
Key 5 '011001001101111110111011110001110111100011010101'
Key 6 '111101111011100101000111001000111000001111111101'

## Password

Final command to clear this level is "tjwyjgdpjw".