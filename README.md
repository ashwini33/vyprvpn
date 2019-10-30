# vyprvpn installation and configuration on amazon EC2 instance
<p>
VyprVPN is a VPN (Virtual Private Network) technology that safeguards your privacy and security with multiple encryption protocols and secure DNS. It provides fast and reliable connections with global network of servers.
</p>
<h3> Why Use a VyprVPN? </h3>
<ul>
  <li>Increase Your Online Privacy and Security :-<br>
    Encrypt your internet connection with VyprVPN to protect your privacy and secure your connection. Prevent your ISP or third-party snoops from viewing your online communications, location and browsing activity.
  <li>Bypass Censorship and Restrictive Networks :- <br>
    Escape government censorship and Internet restrictions,restore your access to a free and open Internet with VyprVPN.
  <li>Stream Without Limitations :- <br>
    Improve your speed, access geo-blocked content, and stay secure while streaming online. Achieve the best streaming experience with VyprVPN.
 </ul>

<p>
  This documentation shows the step-by-step installation of VyprVPN server on AWS (Amazon Web Services).For the VyprVPN own documentation one can follow the <a href="https://support.goldenfrog.com/hc/en-us/articles/360004447451-Deploy-VyprVPN-Cloud-on-Amazon-Web-Services-AWS-"> this </a> link.
 </p>
 
 <p>
  Before getting started, first register for an account on <a href="www.vyprvpn.com"> VyprVPN </a>.
 </p>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/Screenshot+from+2019-07-16+16-18-54.png">
<p>
Choose any plan you want (they provide three day free trail), and confirm your e-mail,once done with account creation go to 
AWS website and log-in in your AWS account.
<p>
  1.Go to EC2 in services section. <br>
  2.Click Launch Instance and follow the below steps. <br>
  3.Choose Ubuntu server 16.04 LTS in setp 1 for choosing AMI.<br><br>
  <img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-36-36.png">
  4.Choose t2.micro as it is in free tier.(you can opt for others also.)<br><br>
  <img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-36-52.png"><br>
  5.In step 3 of configure instance option goto advance option and under option of "User Input" copy and paste the content of this <a href="https://www.goldenfrog.website/downloads/vyprvpn/server/cloud-init.txt">page</a>. <br><br>
  <img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-37-32.png">
  <br>
  6.Configure your security group as given bellow:- <br>
  
  
|Type             |Protocol (auto-set)  |Port Range   |Source|
|:---------------:|:-------------------:|:-----------:|:------:|
|HTTP	            |TCP	                |80	          |My IP (will detect and select your IP)|
|HTTPS	          |TCP	                |443	        |My IP|
|SSH	            |TCP	                |22	          |My IP|
|Custom TCP Rule	|TCP	                |222	        |My IP|
|Custom UDP Rule	|UDP	                |443	        |Anywhere|
|Custom UDP Rule	|UDP	                |500	        |Anywhere|
|Custom UDP Rule	|UDP	                |1194	        |Anywhere|
|Custom UDP Rule	|UDP	                |1701	        |Anywhere|
|Custom UDP Rule	|UDP	                |4500	        |Anywhere|
|Custom UDP Rule	|UDP	                |15001-20000	|Anywhere|
|Custom UDP Rule	|UDP	                |25001-30000	|Anywhere|

<br>
7.Finally launch the instance by either creating or using previous key-pair.<br><br>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-41-27.png"><br>
8.Copy your public IP address and open it in browser ,you will see the VyprVPN installation screen. <br><br>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-41-37.png"><br><br>

9.After the Vyprvpn Server Installation is completed ,enter the public ip py amazon in browser and log-in  with the below credentials :- <br>
```bash
Username: admin
Password: Grod42decK
```
<br>
These are the defaults credentials and need to be changed for security purpose.As it would be your first time logging to this server ,accept the exception and continue.<br><br>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-54-42.png"><br><br>

After successful login ,go to "System Settings" and change the current password.<br><br>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+16-57-13.png"> <br><br>
As of now your server is installed and running set your server name and change the IP type which best suits your instance configuration.<br>
<ol>
  <li>
    If you are using elastic IP attached with your AWS instance or if you are using Digital Ocean droplet then set this value to be Static.As in both the cases if the server reboots the server's IP would not be changed.
   <li>
    If you are not using Elastic IP address with your instance then select Dynamic IP in field of "IP Type".
 </ol>
<br><br>
<img src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot+from+2019-07-17+17-01-05.png"> <br><br>
To connect to the server first install the VyprVPN client ,in the following example we will check the server functioning on Android Device.<br>
First install the VyprVPN on your android device. <br><br>
<img width=320 height=480 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-225637.png"> <br><br>
Open the App and log-in with the new credentials if you have changed.The application will show your current location. Check your current public IP address (search in google or click on  <a href="https://ifconfig.co/"> this </a>
  link to check your current public IP address) . <br><br>
<img width=320 height=600 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-230549.png"><br><br>
<img width=320 height=600 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-231004.png"> <br><br>
Now connect to your sever by selecting the server name (her we have vyprvpn) .<br><br>
<img width=320 height=600 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-230515.png"><br><br>
After you are connected a tiny notification will show you that your device is connected to VPN.<br>
After you connect to the server , again check your public IP if it changed or not.
<img width=320 height=600 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-230651.png"><br><br>
<img width=320 height=480 src="https://gitresource.s3.us-east-2.amazonaws.com/vyprvpn/screenshots/Screenshot_20190717-231039.png"><br><br>

</p>
<hr>
The new IP is changed from India location to US as the instance hosting the VPN server is in the US location.
