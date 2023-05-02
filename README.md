Download Link: https://assignmentchef.com/product/solved-cop4600-ex9-security__trashed
<br>
<h2>Lore</h2>

The Lizard Lords are displeased. The previously developed method of communication via TCP has been breached by humans and messages between Lizards have been intercepted. The Lizard Lords have decided they need a secure way to transmit messages between secret Lizard agents. This is your last chance to be spared the guillotine. You have been tasked with the development of a prototype for a secure communication channel that cannot be broken (not until quantum computers come along?) to demonstrate to the powers that be how humans may be stopped from making any use of intercepted messages.

<h2>Overview</h2>

The aim of this exercise is to familiarize you with asymmetrical encryption. In an asymmetric key encryption scheme, anyone can encrypt messages using the public key of the receiver, but only the receiver can decrypt because only they have access to the private key which is used to unroll the encryption. If the private key of some communication endpoint is obtained, any message pointed towards that endpoint can be decrypted if the public-private key algorithm is known.

<h2>Structure</h2>

To complete this exercise, you will be downloading the provided code skeletons and using one of the websites provided to generate public and private RSA keys. There will be two processes, the first process, <strong>A</strong> shall communicate with a second process <strong>B</strong> via named pipes. Process <strong>A</strong> shall send its public key to process <strong>B</strong> using the pipe. Process <strong>B</strong> then encrypts a message taken via STDIN using this key and sends it back to the first process using another pipe. Then process <strong>A</strong> decrypts this message and displays it.

<ol>

 <li>Use one of these websites to generate RSA keys of size 2048 bits.</li>

</ol>

<a href="https://8gwifi.org/RSAFunctionality?keysize=2048">https://8gwifi.org/RSAFunctionality?keysize=2048</a>  (or) <a href="https://travistidwell.com/jsencrypt/demo/">https://travistidwell.com/jsencrypt/demo/</a>

<ol start="2">

 <li>Save the public key generated in a text file “publicKey.txt” and private key in another text file “privateKey.txt’.</li>

 <li>Take a screenshot of both the files containing the RSA keys side by side.</li>

 <li>Create a named pipe “<strong>pipeEx9</strong>” using the following command.</li>

</ol>

<h3>$ mkfifo pipeEx9</h3>

<ol start="5">

 <li>In “<strong>cpp</strong>”, read the public and a private key from the text files and display the generated keys to the screen. Make use of the helper functions to read the keys. Then send its public key using the named pipe to the second program described in step 6.</li>

 <li>In “<strong>cpp</strong>”, read the public key of the receiver using the named pipe and display it.</li>

 <li><strong>cpp</strong> will take in a string message via STDIN and print it to the console after encryption. After the message is encrypted in sender.cpp, this message will be sent to receiver.cpp via the pipeEx9 created in step 4.</li>

 <li><strong>cpp</strong> will print the received encrypted message, decrypt it and print the decrypted message which should be the same as the initial message passed via STDIN to sender.cpp.</li>

 <li>Take a screenshot of the programs running side by side which should look like the picture below.</li>

</ol>

Three pre-implemented helper functions have been provided along with the templates. You can use these to assist in your coding or implement your own functions for reading and converting the keys.




<ol>

 <li><strong>char* readKey(string fileName) – </strong>reads the key from the text file and stores it in a char pointer</li>

 <li><strong>RSA* convertPrivateKeyToRSA(FILE* fp, int length)- </strong>converts private key in string format to RSA format</li>

 <li><strong>RSA* convertPublicKeyToRSA(FILE* fp, int length)- </strong>converts public key in string format to RSA format</li>

</ol>

<strong> </strong>

<h2>Submissions</h2>

You will submit the following at the end of this exercise on Canvas:

<ul>

 <li>C++ source file for receiver.cpp</li>

 <li>C++ source file for sender.cpp</li>

 <li>Makefile to compile the two programs</li>

 <li>Screenshot of public and private key text files described in the steps above.</li>

</ul>







<strong><em>Figure 1: An example screenshot of the RSA key files </em></strong>

<ul>

 <li>Screenshot of the output from running the demo described in the steps above.</li>

</ul>







<strong><em>Figure 2: An example screenshot with output from running the solution. </em></strong>

<strong><em> </em></strong>

<strong>NOTE 1: Use RSA_PKCS1_OAEP_PADDING for the padding mode for encryption and decryption (which takes 42 bytes). </strong>

<strong>NOTE 2: The maximum number of bytes you can encrypt for a 2048 bits modulus is 256 bytes – </strong>

<strong>42 bytes (for padding) = 214 bytes (so 213 total characters + 1 null terminator) when using RSA_PKCS1_OAEP_PADDING. Be mindful of null terminators. </strong>

<strong><em> </em></strong>

<strong> </strong>

<h2>Helpful Links</h2>




<a href="https://www.ibm.com/support/knowledgecenter/en/SSB23S_1.1.0.13/gtps7/s7pkey.html">https://www.ibm.com/support/knowledgecenter/en/SSB23S_1.1.0.13/gtps7/s7pkey.html</a> <a href="https://www.openssl.org/docs/man1.0.2/man3/rsa.html">https://www.openssl.org/docs/man1.0.2/man3/rsa.html</a>

<u>https://medium.com/swlh/understanding-asymmetric-public-key-cryptography-24092bcd7741</u>