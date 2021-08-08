It is given that it is a RSA encryption. So, <br/>

- C = M<sup>e</sup>mod(n)
- M = C<sup>d</sup>mod(n)

where,
C is encrypted message,
M is message

e = 5

n = 84364443735725034864402554533826279174703893439763343343863260342756678609216895093779263028809246505955647572176682669445270008816481771701417554768871285020442403001649254405058303439906229201909599348669565697534331652019516409514800265887388539283381053937433496994442146419682027649079704982600857517093

C = 23701787746829110396789094907319830305538180376427283226295906585301889543996533410539381779684366880970896279018807100530176651625086988655210858554133345906272561027798171440923147960165094891980452757852685707020289384698322665347609905744582248157246932007978339129630067022987966706955482598869800151693

We can find factors of n to decode the above password, but we can't because n is too long. We may still attempt to compute d, but since n could not be factored, we cannot do so effectively.

For a small public exponent (e = 5), it is clear that the low public exponent attack method, called the LLL lattice basis reduction algorithm (Coppersmith’s Algorithm), can be used.

For this algorithm to work, we first need to check if padding is added to the message. This can be easily checked if this expression : C<sup>1/e</sup>mod(n) gives an integer value. If it does not yield an integer, then we concluded that padding is added.

We computed the same and found that padding is added. Let p be the padding. Thus the final equation becomes:
(p+M)<sup>e</sup> = Cmod(n)

We use the encoded part (hexadecimal system) to reach the problem and use it as padding, i.e., 'You see a Gold-Bug in one corner. It is the key to a treasure found by ' (“ ” character after “by”)

We created the polynomial using given information (C, e and message) which was the input to the algorithm, and then we reduced the polynomial using the LLL algorithm as follows :

1. Firstly, we let N be an integer and f be polynomial of degree δ. Given N and f, one can recover polynomial times all x<sub>0</sub>​ such that f(x<sub>0</sub>​) = 0 mod(N). So we took
   f(M)=(p+M)<sup>e</sup>mod(N) as our polynomial equation.
2. To deal with padding p, we converted it to binary form so that it could be used in the final polynomial expression.
3. As we do not know the length of the password P, we can at least show that the length cannot be longer than 300, as we can conclude from our assumption x<sub>0</sub> < N<sup>1/e</sup>.
4. The final polynomial is pol = ((padding_binary << len_P)+P)<sup>e</sup> − C.
5. Then found the roots of that polynomial. The root found by the modified coppersmith’s algorithm was : 0100001001000000011010000111010101100010010000010110110000100001.

This gives us a string of binary numbers, using ASCII value we convert it to character and then got the password (B@hubAl!).

References:

1. https://en.wikipedia.org/wiki/Coppersmith%27s_attack
2. https://github.com/mimoo/RSA-and-LLL-attacks/blob/master/coppersmith.sage
