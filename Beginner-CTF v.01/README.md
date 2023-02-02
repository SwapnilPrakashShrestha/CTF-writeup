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


### Q4) After Steg the path was.
### Ans: welldone
We again see same two images in the next directory so i guess its more seganography. Though to download the files we cannot use download button. 
First we need to inspect the page and then download it.
1.jpeg is just to waste the time and nothing can be found under it and when running **exiftool** in the 2.jpeg we find the following outcome.
![image](https://user-images.githubusercontent.com/68239030/216247515-0103de39-949d-40f2-9cbb-899e4cc86e76.png)

Therefore the next directory is :
>https://swapnilshrestha.com.np/5/htmlcomment/welldone


### Q5) Which tool did you use to find the user?
### Ans: Sherlock

![image](https://user-images.githubusercontent.com/68239030/216248038-9418c7fa-955d-459f-ae74-2e43fe8187b0.png)
According to the picture we need to find where username **NakaliShrestha1** is? 
Using **sherlock** we can find the social media to that username
>sherlock NakaliShrestha1

We see different social site in which **twitter** is the what we are after.
![image](https://user-images.githubusercontent.com/68239030/216248994-57dc327f-0ade-4608-aa08-2ede62e863d8.png)

There is a random text i.e  **c2hyZXN0aGExMjM0NW5ha2FsaQ==**  , When enterd in [CyberChef](https://gchq.github.io/CyberChef/) spits out **shrestha12345nakali**.
This username is again entered in sherlock and a list is shown in which **Houzz** is only valid.
![image](https://user-images.githubusercontent.com/68239030/216250230-e3387621-c9e2-45e6-acb3-dd8bde2344d2.png)

There is a ideabook called flag and the next directory is **sherlock101**
>https://swapnilshrestha.com.np/5/htmlcomment/steg/welldone/sherlock101

### Q6) What did you change to go the the directory /james_bond ?
### Ans: user-agent

![image](https://user-images.githubusercontent.com/68239030/216251143-7dc4c056-4c09-481e-a42c-4e5a6103c3ce.png)

Here we need to change the user-agent as in the image we can see only **Nakali_Shrestha** can access the next page
To change the user agent : 
1) Right Click Anywhere in Webpage > Inspect. Alternatively, you can use CTR+Shift+I on Windows, Cmd + Opt +J on Mac.
2) Choose More Tools > Network Conditions. ...
3) Uncheck Select Automatically Checkbox.
4) Use custom user-agent, Nakali_Shrestha

![image](https://user-images.githubusercontent.com/68239030/216252594-59afa70a-f4d2-4090-9ad9-143d5834c34c.png)

5)Enter the url with costum user-agent : https://swapnilshrestha.com.np/5/htmlcomment/steg/welldone/sherlock101/james_bond


### Q7) Which was the application to view the link (not the QR) ?
### Ans: google maps

>https://swapnilshrestha.com.np/5/htmlcomment/steg/welldone/sherlock101/james_bond/glocation

### Q8) What was the passphrase of the website? 
### Ans: client-site is fun
We see the next phase of the CTF as a Client-Side Authentication.
![image](https://user-images.githubusercontent.com/68239030/216253489-029f7332-cef5-4237-989d-6c2269dba35d.png)

When we try to login with a random password we see the username is **admin**. ![image](https://user-images.githubusercontent.com/68239030/216253694-dc8475e8-7a78-4739-997c-768756aae450.png)

but username: admin password: admin doesnt work. 
When we inspect the page we can see that the browser is verifying the authentaction process and its using user's entered password with **Y2xpZW50LXNpdGUgaXMgZnVu** to check it
**Y2xpZW50LXNpdGUgaXMgZnVu**  When enterd in [CyberChef](https://gchq.github.io/CyberChef/) spits out **client-site is fun**
![image](https://user-images.githubusercontent.com/68239030/216258456-86f582fc-f790-4eca-be1f-682a22bbb12a.png)


### Q9)  What was the name of the file where you found first half of the next directory?
### Ans: robots.txt
![image](https://user-images.githubusercontent.com/68239030/216258952-eee16d63-c1b9-4036-9b5a-fb4e8010e73d.png)

If we click on the icon we go the [Site](https://www.youtube.com/watch?v=dQw4w9WgXcQ) and get Rickrolled!
Its a page where its talks about **robots.txt** and going to the robots file of the page leads to first half of the final directory: 
![image](https://user-images.githubusercontent.com/68239030/216259798-b7c68b4f-a6c3-4499-bee8-dfdfc0762399.png)

### Q10)  The final directory was?
### Ans: robots_and_caesar_cipher

The first part of the final directory was found in Question 9 and for the last part we need to rotate **gtj_igkygx_iovnkx** on [caesar cipher](https://www.dcode.fr/caesar-cipher) and we get the final part of the directory "and_caesar_cipher".
so the final directory is: [Here](https://swapnilshrestha.com.np/5/htmlcomment/steg/welldone/sherlock101/james_bond/glocation/client-site_is_fun/robots_and_caesar_cipher)
![image](https://user-images.githubusercontent.com/68239030/216261104-76417e76-e3d4-48d2-9e1b-25e0ccdd34fc.png)

