# DVD Rental

### <em>Video Walkthrough: </em>https://youtu.be/jQ7rpQ4HABs
<a href="https://youtu.be/jQ7rpQ4HABs">
<img src="https://user-images.githubusercontent.com/107213928/213590644-30eb6bda-fa01-433a-9c49-9b395832176e.png" alt="video walkthrough"></a>


## Introduction:
This project uses the DVD Rental sample database included in PostgreSQL.  The scenario is that of the DVD Rental Company inventory manager who wants to determine how many copies of each DVD should be stocked on the shelves.  To make this decision, the manager needs to know which DVDs are rented most frequently, and how many days they are rented for.  This information needs to be store-specific because each store has their own stock of DVDs on the shelves.  

The data used for the report includes rental information about the DVDs, such as the dates rented and returned. It also includes information identifying which store the DVDs are from, and what films they are.  

There are two source tables needed to provide the data necessary for the detailed and summary sections of the report.  These tables are the rental table and the inventory table.  The two new tables created are the rental_detail, and rental_summary tables.

The fields that are included in the detailed and summary reports from the source data rental table are the rental _id, rental_date, and return_date fields.  The fields included from the source data inventory table are the the store_id field, the film_id field.  

A data transformation included is the days_rented_out field in the detailed report which calculates the difference, in days and time, between the rental_date, and the return_date fields from the rental table. The days_rented_out field allows the inventory manager to quickly identify DVDs which were kept for an especially long period of time, and which were therefore unavailable for rental during that time.  

The detail table provides a record of every rental record in the report.  This will be useful because it will indicate how many total rentals have taken place.  It will also show the number of days that a DVD was rented out for each rental.  The summary table shows the total number of times rented for each DVD (film_id) at each store.  

The report should be refreshed bi-weekly.  The inventory manager needs to decide how often to evaluate the relative popularity of DVD titles to adjust and optimize the stock levels accordingly.  If he does it too often though, weekly for example, it will take too much time away from other duties while providing relatively little benefit.  However, monthly wouldn’t be frequent enough because the popularity of movie titles is likely to fluctuate significantly over a one-month span.  


## Project execution screenshots:
1. Download the Unbutu Linux desktop ISO file. 

![step 1](https://user-images.githubusercontent.com/107213928/187050374-7c679587-2d92-4809-9f95-3ed6c1b6887b.png)

2. Install the Unbutu Linux desktop ISO file on WMWare Fusion. 

![step 2](https://user-images.githubusercontent.com/107213928/187050409-ab0b695b-4548-436b-93f2-c90ebd9a0994.png)

3. Accept default configurations for the virtual machine while installing Unbutu.  Boot up the Unbutu Desktop, click on your account name, and enter the password you set during installation to log in.  become familiar with the interface.  

![step 3](https://user-images.githubusercontent.com/107213928/187050687-9de4ab04-0a96-4225-ac64-d9451ddda92c.png)
![step 3 2](https://user-images.githubusercontent.com/107213928/187050701-cf1c6945-984d-4d96-ad7e-644d8370fcc2.png)

4. Click on the 9-dot icon in the bottom left of the screen to open the apps menu, and click on the  Terminal App icon to open the terminal.

![step 4](https://user-images.githubusercontent.com/107213928/187050726-97ccfe37-9be8-48bf-8bf0-abfaf8e92115.png)

5. Enter the command, sudo apt-get update to ensure that Ubuntu is up to date.  Enter account password when prompted.

![step 5](https://user-images.githubusercontent.com/107213928/187050750-6bd0bc86-2dc3-4c7f-bb0d-47a34ebb82b6.png)

6. Open the files app, and add the files you’d like to share to a directory.  In this project, I will add English teaching materials to the /home/documents directory.

![step 6](https://user-images.githubusercontent.com/107213928/187050774-4e3f888e-3613-4678-a860-86b50197128a.png)

7. To make files accessible by colleagues located in different physical locations, set up Apache web-server.  Open the terminal again, and enter the command, sudo apt install apache2.

![step 7](https://user-images.githubusercontent.com/107213928/187051870-910ddb61-b148-406e-8815-de82c15b4c5e.png)

8. The Apache web-server should already be running after the installation is complete.  Confirm that Apache is running by checking the status with the command, sudo systemctl status apache22.  The output should indicate that the status is active.

![step 8](https://user-images.githubusercontent.com/107213928/187051896-aa6584b8-11b9-45f0-b8ed-ff020fa289aa.png)

9. Confirm that the Apache web-server is running properly by accessing the default Apache landing page.  To do this, you can either enter “localhost” into the address bar, or you will need to know your server’s IP address.  Get the IP address by running the command, hostname -.

![step 9](https://user-images.githubusercontent.com/107213928/187051919-88b1f228-5125-4c36-a27e-8d854b19d65a.png)

10. Test Apache by opening a web browser, like Firefox, and enter it after http://.  For example, http://172.16.7.130.  You should see the default Apache landing page. 

![step 10](https://user-images.githubusercontent.com/107213928/187051943-51e47ad7-d977-4840-ac5c-8fd098874afd.png)

11. Now that the correct functioning of Apache is confirmed, return to the terminal and remove the index.html file from /var/www/html with the command, 
sudo rm /var/www/html/index.html8.

Next, copy the documents directory to /var/www/html with the command, sudo cp -r /path/to/directory /var/www.html/[insert new directory name].  For example, sudo cp -r /home/kushmirchandani/Documents /var/www/html/EnglishTeachingMaterials.

![step 11](https://user-images.githubusercontent.com/107213928/187051966-8fb7850e-339f-422b-b264-124774e8f6e9.png)

12. Open the web browser again and refresh the page at http://172.16.7.130, or simply type “localhost” in the address bar.  You should now see a navigable index of the files.

![step 12](https://user-images.githubusercontent.com/107213928/187051980-12debcf6-0564-467d-96ac-c9123b1dc202.png)
![step 12 2](https://user-images.githubusercontent.com/107213928/187052000-f3e71f36-e3d6-4f84-9320-977a16184e29.png)

<em>The above steps provide us with a directory of documents that can be shared with colleagues.  To create a searchable database with a WebUI interface, I will take the next steps to intall Recoll.</em>

13. Install the Recoll repository and software by running the following 3 commands in the terminal:
	sudo add-apt-repository ppa:recoll-backports/recoll-1.15-on
  sudo apt-get update 
  sudo apt-get install -y recoll python-recoll

![step 13](https://user-images.githubusercontent.com/107213928/187052032-ce7055d1-c33a-4751-a229-1347816d9aaf.png)
![step 13 2](https://user-images.githubusercontent.com/107213928/187052043-80541b3a-db2e-4234-a23b-cc5d9f91c903.png)

14. Install mod-wsgi with the command, sudo apt-get install -y libapache2-mod-wsgi
The mod-wsgi package implements an Apache module which can host Python web applications, which is necessary because Recoll is in Python.

![step 14](https://user-images.githubusercontent.com/107213928/187052061-ded71eee-5aa7-4e71-b863-2f670ecf8d08.png)

15. Download the Recoll webui from the Github repository at the following url:
https://github.com/koniu/recoll-webui
Click the applicable hyperlinked zip file to download the archive, and extract it to your /var/www directory. It should create the folder 'recoll-webui-master'.

![step 15](https://user-images.githubusercontent.com/107213928/187052085-418303de-bcf0-4d82-bceb-649181fe3ee4.png)
![step 15 2](https://user-images.githubusercontent.com/107213928/187052098-6385a856-e95b-4702-80e2-9d4aa3bc6565.png)

16. Next edit the file, /etc/apache2/mods-enabled/wsgi.conf by adding the following at the end of the "IfModule" section:

WSGIDaemonProcess <strong>recoll user=web_user</strong> group=root threads=1 processes=5 display-name=%{GROUP} python-path=/var/www/recoll-webui-master
WSGIScriptAlias /recoll /var/www/recoll-webui-master/webui-wsgi.py

Alias /static /var/www/recoll-webui-master/static

&lt;Directory /var/www/recoll-webui-master&gt;<br>
        WSGIProcessGroup recoll<br>
        Order allow,deny<br>
        allow from all<br>
&lt;/Directory&gt;

Put the code shown above just above of closing tag: </IfModule> in the wsgi.conf file7.  You must change the user to the user who’s files you want to make available. For example, I have changed the user to kushmirchandani.

WSGIDaemonProcess <strong>recoll user=kushmirchandani</strong> group=root threads=1 processes=5 display-name=%{GROUP} python-path=/var/www/recoll-webui-master

17. After completing the steps above, you should be able to see Recoll in the Apps menu (make sure to display “All” apps, and not the “Frequent” apps which may be selected by default). Open Recoll.

![step 17](https://user-images.githubusercontent.com/107213928/187052300-3b8fac49-9dda-4929-95b7-e964ec21b6ec.png)

18. Upon opening Recoll, you will be asked whether you would like Recoll to index the home directory, or whether you would like to adjust the indexing configuration.  Click the “Start indexing now” button to accept the default configuration.  Or, you set the index to just the Documents folder within the home directory now, or at a later time. 

![step 18](https://user-images.githubusercontent.com/107213928/187052318-91d650c2-c836-47fc-8432-d7c6615f08b4.png)

19. Select “OK” on the prompt asking whether you would like to reset the index. 

![step 19](https://user-images.githubusercontent.com/107213928/187052341-624a82c9-6cab-493b-87cb-3ea50cb8b87c.png)

20. Select “OK” again when notified about Missing helper programs.  

![step 20](https://user-images.githubusercontent.com/107213928/187052356-7896fdcf-0adf-4b45-8a7c-87e2636866e6.png)

21. Now that Recall is installed and configured we can access it in a web browser.  First, restart Apache to ensure that the changes made above are active with the following command in the terminal, sudo systemctl restart apache2.

![step 21](https://user-images.githubusercontent.com/107213928/187052388-7794bb46-ff79-40b3-b697-6189f49915eb.png)

22. Open the web browser again.  This time, in the address bar, instead of just typing “local host” or your IP address, add /recoll/ to the end of it.  For example, http://localhost/recoll/.  You will arrive at the WebUI for Recoll.

![step 22](https://user-images.githubusercontent.com/107213928/187052412-8e9421fe-d5e1-4eb5-abb2-124a69cca335.png)

23. Using the search bar in Recoll, you are now able to perform various searches for files.  For example, you can search by file type by entering “*.pdf”.  Or, you can search the full content of files for desired keywords, such as “business”.

![step 23](https://user-images.githubusercontent.com/107213928/187053496-4e2197b9-1770-4c97-b2ce-78c27625ffc7.png)
![step 23 2](https://user-images.githubusercontent.com/107213928/187053503-4f394274-3b89-4329-9b80-3bda6ad52299.png)

### Troubleshooting Tips:
•	Step 11:  If you’re unable to remove the .html file from /var/www/html, you may need to add permissions to write to this file.  You can do this with the following command, 	
sudo chmod -R 757 /var/www/html3

•	Step 16:  If you’re unable to edit the /etc/apache2/mods-enabled/wsgi.conf file, you may need to add permissions.  You can do this with the following command, chmod +rwx directoryname to add permissions.  For example, chmod +rwx /etc.

•	Step 21:  If you get an error when running the sudo systemctl restart apache2 command, you can also stop and then start Apache with the following commands, sudo service apache2 start and sudo service apache2.

•	Step 23:  If you’re unable to view files in the Recoll WebUI in Firefox, you may need to edit the Firefox <profile> file to authorize Firefox to open local files.  Include the following in the /.mozilla/firefox/<profile>/user.js file (in the home directory):
	
   user_pref("capability.policy.policynames", "localfilelinks");<br>
   user_pref("capability.policy.localfilelinks.sites", "http://localhost:8080");<br>
   user_pref("capability.policy.localfilelinks.checkloaduri.enabled", "allAccess");<br>
	
If you can’t find a <profile> file, you may need to create your profile.  Instructions for creating a profile can be found here: https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles9

