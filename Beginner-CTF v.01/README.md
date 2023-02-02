### Beginner-CTF Writeup

![360_F_442875732_pLZxb6cPjE3hhGwWAowvvoU87vQj5Q7k](https://user-images.githubusercontent.com/68239030/216055661-14b53aa5-ab35-4a01-ae01-0dcbcf6e5111.jpg)

 The aim of this CTF was to educate young learners on security concepts and help them develop practical skills in area such as cryptography and web security.

For those who want to play the CTF , challenges are still available at:
### https://swapnilshrestha.com.np
and question are avilabel at https://tryhackme.com/room/ctf2023

### Solution starts here!
### Q1) Which was the First correct Directory?
### Ans: 5
When we fisrt open the site we are welcomed with the page which tells us to go the the final door in the hallway. When we hover over the door Md5 hash is shown.
![image](https://user-images.githubusercontent.com/68239030/216240521-4306aa4e-9a4c-482f-b35f-79376d4e3a5a.png)
when we inspect the page with following command we see: 
> ctrl + u

![image](https://user-images.githubusercontent.com/68239030/216240660-be489eae-4656-46c7-87fb-db7fe2c214d9.png)

Telling us that its a md5hash and the door its has a hash of 5 when checking it on  **https://crackstation.net**

So the next directory of the CTF is:
> https://swapnilshrestha.com.np/5

### Q2) Did you get the next directory?
### Ans: htmlcomment
For the next part we see the following : 
![image](https://user-images.githubusercontent.com/68239030/216241429-2149372b-800d-4af8-98db-2bc58d802675.png)

When we inspect (ctrl + u) the page we can see that the next directory is /htmlcomment which is commented out.
![image](https://user-images.githubusercontent.com/68239030/216241612-03b70b95-3d99-47cc-8456-29a8415eff38.png)
>https://swapnilshrestha.com.np/5/htmlcomment

### Q3) The next Path was.
### Ans: steg

The next page gives us a image and is about steganography. After downloading the image we can use **steghide** to extract hidden text file in the image with passphrase as blank(given in css comments). 

>wget https://swapnilshrestha.com.np/5/htmlcomment/steganographhy.jpeg
>
> steghide --extract -df steganograpgy.jpeg
> 
> ls
> 
> cat hidden.txt


Spits out: The next dierctory is **/steg**
