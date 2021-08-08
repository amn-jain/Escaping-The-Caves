From the given three pairs we firstly calculate the value of ‘g’ and from that we calculate the password.
<br/>
For the analysis, here are some terminology :

- (a<sub>i</sub> ,b<sub>i</sub>) where this pair is the given tuple, where i belongs to [0,1,2] <br/>
- p is the given prime number with with we are taking modulo <br/>
- g is same as given in the ciphertext
- pd is the password

Let x<sub>0</sub>,x<sub>1</sub>,x<sub>2</sub> ​be some integers,

And to find ‘g’, let

> b<sub>0</sub><sup>x<sub>0</sub></sup> . b<sub>1</sub><sup>x<sub>1</sub></sup> . b<sub>2</sub><sup>x<sub>2</sub></sup> = g

On putting b<sub>i</sub> = pd.g<sup>a<sub>i</sub></sup> <br/>

> (pd . g<sup>a<sub>0</sub></sup>)<sup>x<sub>0</sub></sup> . (pd . g<sup>a<sub>1</sub></sup>)<sup>x<sub>1</sub></sup> . (pd . g<sup>a<sub>2</sub></sup>)<sup>x<sub>2</sub></sup> = g

On Simplifying

> pd <sup>x<sub>0</sub>+x<sub>1</sub>+x<sub>2</sub></sup> . g <sup>a<sub>0</sub> x<sub>0</sub> + a<sub>1</sub> x<sub>1</sub> + a<sub>2</sub> x<sub>2</sub> </sup> = g

On Equating we get,

> x<sub>0</sub> + x<sub>1</sub> + x<sub>2</sub> = 0<br/>
> a<sub>0</sub>x<sub>0</sub> + a<sub>1</sub>x<sub>1</sub> + a<sub>2</sub>x<sub>2</sub> = 1

Also we assume x<sub>i</sub>​ to be an integer.<br/>

We put x<sub>0</sub>=−x<sub>1</sub>−x<sub>2</sub>​ in the second equation.
And by changing x<sub>1</sub>​ between -1000 to 1000 (just a random range), we try to find integer value of x<sub>2</sub>​.
From this we get the values of all x<sub>i</sub>’s.

Now in eq.

> b<sub>0</sub><sup>x<sub>0</sub></sup> . b<sub>1</sub><sup>x<sub>1</sub></sup> . b<sub>2</sub><sup>x<sub>2</sub></sup> = g <br/>

Only unknown is g. And from this we get the value of g and verify it from the given hint.

After that, to find the password we use eq. b<sub>i</sub> = pd . g<sup>a<sub>i</sub></sup>​. And verify that password is same for all value of i. We get all three value same and got the password.
