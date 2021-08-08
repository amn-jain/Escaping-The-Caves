The above-specified sequence of commands leads us to the glass panel which gives us the information regarding the cryptanalysis technique used i.e EAEAE. The text specified that the input block is of 8 bytes as a vector over F<sub>128</sub>​ constructed using degree 7 irreducible polynomial x<sup>7</sup> + x + 1 over F<sub>2</sub>​. It also specified 2 transformations :

- A : a linear transformation given by invertible 8 x 8 key matrix A with elements from F<sub>128</sub>​
- E : exponentiation given by 8 x 1 vector E whose elements are numbers between 1 and 126

Note : E is applied on a block by taking the i<sup>th</sup> element of the block and raising it to the power given by the i<sup>th</sup> element in E.

We tried many inputs and saw that the output only has some limited letters, i.e. from 'f' to 'u'. Then by observing each block of 2 letters, we concluded that the encryption is from 'ff' - 'mu' (this even has 128 characters).
Then we decided to keep inputs as follows :
"ffffffffffffffff", "ffffffffffffffgg", "ffffffffffffggff", and so on.
We observe that changing the i<sup>th</sup> byte of the input changes all the bytes of output after the i<sup>th</sup> byte. This implies that the i<sup>th</sup> byte is not used in computing the output values at byte number 0 to i - 1. From this, we concluded that the transformation matrix used here must be lower triangular.

After this we started to find the diagonal elements of matrix A and also vector E. For this we derived an equation which contains only i<sup>th</sup> diagonal element and i<sup>th</sup> element of vector E. The equation is y<sub>i</sub> = (a<sub>ii</sub> ( a<sub>ii</sub> . x<sub>i</sub><sup>e<sub>i</sub></sup> ) <sup>e<sub>i</sub></sup> ) <sup>e<sub>i</sub></sup>​ . This equation is valid only if the i<sub>th</sub> byte of x<sub>i</sub>​ (input) is non zero and all other bytes are zero.

Now we used a fixed pair of input to calculate the possible values of e<sub>i</sub>​ and a<sub>ii</sub>​. We choose x<sub>i1</sub> = 1 and x<sub>i2</sub> = 2. Now after taking the ratio of y<sub>i1</sub> and y<sub>i2</sub>​ we get 2<sup>e<sub>i</sub><sup>3</sup></sup>. This gives 3 possible values of e<sub>i</sub>​ (since it is a cubic equation) and correspondingly we get 3 possible values of a<sub>ii</sub>.

{ '24, 84', '75, 96', '28, 46'}<br/>
{'105,70', '59,127', '90,9'}<br/>
{'29,108', '43,43', '55,86'}<br/>
{'15,68', '31,95', '81,12'}<br/>
{'85,31', '78,5', '91,112'}<br/>
{'96,71', '112,125', '46,11'}<br/>
{'88,63', '18,123', '21,27'}<br/>
{'28,33', '24,38', '75,53'}<br/>
were the possible pairs respectively.

Now, it is not easy to find the right pair. For this we start to find the value of elements of the form a<sub>i,i-1</sub>. For finding this we selected 2 input pairs with value 1 and 2 at (i−1)<sub>th</sub> byte and rest byte as zero. Now the equation for finding a<sub>i,i-1</sub>​ will have dependency on a<sub>i ,i</sub> , a<sub>i-1,i-1</sub> , e<sub>i</sub>​ and e<sub>i-1</sub>​. Now we choose a pair from the 3 possible values and try to find the value of a<sub>i,i-1</sub>. Now only the right combination gives the value of a<sub>i,i-1</sub>​. In this way we get the value of diagonal elements and the vector E along with a<sub>i,i-1</sub>.

Now finding the rest of elements was an easy task because we have all a<sub>i,i</sub>​ and a<sub>i,i-1</sub> and vector E. We start finding in order a<sub>i,i-2</sub> & a<sub>i,i-3</sub>​.... and so on. Again using the same method as of a<sub>i,i-1</sub>​ we found the value ofa<sub>i,i-2</sub>​. And so on.

For the a<sub>7,0</sub>​ we get 3 possible values. And for all three values, we found the password and we got 3 values of password. We checked all three values of the password to get the right one.

The matrix A and vector E were found to be:

![](images/matrix.png)

After calculating the inverse of matrix A i.e. A’ and the inverse of Exponential function E i.e. E’, the decryption becomes E’A’E’A’E’. Now we tried to decrypt the password using this decryption algorithm but it didn’t work. So we converted it into bits and used ASCII values, and then we got “xjtwcsnucg000000”. We removed extra zeros (as we thought 0’s were just for padding) from the end and it worked.<br/> Thus the password we got is: xjtwcsnucg
