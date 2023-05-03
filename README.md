Download Link: https://assignmentchef.com/product/solved-cs3339-lab-1-public-and-private-keys-and-sending-encrypted-messages
<br>
In this lab we will be creating a public and private key pair and sending encrypted messages. However, first we will be installing the software that we will be using for labs this semester.

<ol>

 <li>Download and install Virtualbox if you do not already have it on your computer <strong>https://www.virtualbox.org/wiki/Downloads</strong> (or the hypervisor of your choice)</li>

 <li>Download the Kali Linux VM. Kali is a distro of Linux that comes pre-installed with a variety of security tools. This is what we will be using for many of the labs in this class. An image that is already set up is available here: <a href="https://s2.smu.edu/~dphanekham/CS3339/CS3339.ova">https://s2.smu.edu/~dphanekham/CS3339/CS3339.ova</a></li>

 <li>Open Virtualbox. Go to file→Import appliance and find the CS3339.ova file that you have just downloaded. You can increase its RAM and change other configuration options in the Virtualbox settings.</li>

 <li>Start the VM and log in.</li>

</ol>

username: <strong>root </strong>password: <strong>CS3339</strong>

<ol start="5">

 <li>You should be able to change the display size in the Display settings in the virtual machine.</li>

 <li>Once that is done enter the command <strong>gpg –gen-key</strong></li>

 <li>then it will ask for your information Enter your name, email, and a comment</li>

 <li>It will then ask you to help create entropy (randomness). You can do this by opening up a text editor and randomly typing in characters until the process completes.</li>

 <li>After this process completes, you now have a public/private key pair. We will be talking about how these work more in class, but in practice, you want to keep your private key private and you can publicly distribute your public key, as the names imply. If something is encrypted using your public key, then it can only be decrypted using your private key, this way people can send you encrypted messages that only you can read. Additionally, you can digitally sign files with your private key.</li>

 <li>Run the following command to export your public key to a file. <strong>gpg –armor –export </strong><strong><u><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="c8b1a7bdbaada5a9a1a488a9acacbaadbbbbe6aba7a5">[email protected]</a></u> &gt; firstname_lastname_pubkey</strong></li>

 <li>Create a new file and name it plain.txt. At the top of this file, put your full name. Beneath that, write some lines of text (it doesn’t matter what really) and save it.</li>

 <li>Navigate to where you saved plain.txt and run the command <strong>gpg –encrypt –armor -r <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="aed7c1dbdccbc3cfc7c2eecfcacadccbdddd80cdc1c3">[email protected]</a> plain.txt</strong></li>

</ol>

This command is encrypting the file plain.txt using your public key.

<ol start="13">

 <li>You now have a new file called plain.txt.asc. This is the encrypted text. If you open it, you can see it looks like random characters.</li>

 <li>To decrypt the file, use the command <strong>gpg plain.txt.asc</strong></li>

</ol>

Save the decrypted file as decrypted.txt

This command has decrypted the file using your private key.

Only your private key can decrypt a file that was encrypted using your public key

<ol start="15">

 <li>In reality, you would send your public key to other people or publish it to make it known to everybody. Now whoever has your public key can send you a message that only you can read.</li>

 <li>Now you are going to send me an encrypted message. First you need to add my public key. Download my public key from <a href="https://s2.smu.edu/~dphanekham/CS3339/dphanekham_pubkey">https://s2.smu.edu/~dphanekham/CS3339/dphanekham_pubkey </a>and enter the command: <strong>gpg –import dphanekham_pubkey</strong></li>

 <li>Now encrypt plain.txt using my public key.</li>

</ol>

<strong>gpg –encrypt –armor -r <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b2d6c2dad3dcd7d9dad3dff2c1dfc79cd7d6c7">[email protected]</a> plain.txt </strong>and save it as dphanekham_encrypted

<strong>DELIVERABLES</strong>

A .zip folder named LAB1_Lastname_Firstname.zip containing:

<ul>

 <li>your public key (firstname_lastname_pubkey)</li>

 <li>txt</li>

 <li>txt.asc</li>

 <li>txt</li>

 <li>dphanekham_encrypted</li>

</ul>