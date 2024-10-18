---
---
## [[Table of Contents]]

* **HTML & CSS** - front end design and layout
* **PHP** - back end management
* **SQL** - relational database management system
* **Javascript** - link between front end and back end
* **jQuery** - JS library to help with notation and ease

### Dynamic Web Page Linking

1. JS determines needed data and sends request
2. PHP receives request and passes it to MySQL database
3. MySQL uses SQL to retrieve requested data and returns it to PHP script
4. PHP reads SQL data into Javascript Object Notation (JSON)
5. JS displays the JSON file data

### Web App vs Website

While a web app is also a website, not all websites are web apps. Similarly to a desktop application, a web app is a website that has an intended purpose and is often dynamic in that it allows the user to complete a set of tasks associated with the application. However, a website in and of itself is simply a hosted server that displays information.

### Key Terms Surrounding Websites

* Storage
	* Simply put, how much data can be hosted for a server
	* Larger storage pace = more files and thus a larger websites
	* Different components take different amounts of storage -> Coding in HTML and CSS might not take a lot of storage, but including a picture will rapidly eat up storage
	* Outsourcing will usually limit how much storage is available
* Bandwidth
	* How much data the server/website can send out
	* If one page requires a total of 25KB to display/function, the bandwidth consumed for that page would be 25KB
	* If 10 people access that page, then the total bandwidth involved would be 250KB
	* Outsourcing the hosting of the website will usually lead to a cap being implemented on the bandwidth
* Domain name
	* The site, URL, internet address
	* Regular vs sub
		* A regular domain name might look something like [instagram.com](http://instagram.com)
		* A subdomain name might look like [calendar.pythonanywhere.org](http://calendar.pythonanywhere.org)
	* Using a regular domain name requires that you register the domain name some way, whether that be through GoDaddy, [Register.com](http://Register.com), or somewhere else
	* Registering a regular domain name will typically include a fee, thus people will take on subdomain names that are cheaper
		* In above example, pythonanywhere is the web hosting company, and calendar would be your personal name
* Email Addresses
	* Hosts may offer email addresses along with your web space, larger payments -> more mailboxes and sometimes email forwarding routing that allows messages sent to web host address to be routed to another email address
* Shared server
	* Some hosts may offer a shared server in which you would be sharing a server with other websites
	* Web host manages server management, whereas your only personal commitment is maintaining your personal site
	* Typically cheapest and easiest plan
* Dedicated server
	* You get your own server computer from the web host
	* You are personally responsible for managing the server
	* Oftentimes more expensive than a shared server
* Operating system
	* Web servers will typically have 1 of 2 operating servers, Windows or Unix
		* Unix servers are typically reliable and fast even against heavy web traffic, typically more optimal for a shared server
		* Windows servers are easier to manage than Unix servers, and thus may be better suited for a Dedicated server
		* Unix is case sensitive for file and directory names, Windows servers are not
* Databases
	* Unix systems typically offer MySQL databases whereas Windows servers would offer SQL server databases
* Administration Interface
	* Host app used to perform tasks on the server(uploading files, creating users)
	* cPanel interface is popular and phpMyAdmin is popular among Unix-based systems
* Uptime
	* Uptime refers to the percentage of time that the host's server is up and running
	* All servers require some maintenance, so no server will have 100% uptime
	* Ideally, a host should have 99%< uptime or somewhere in that range to have reliable service
* FTP Support
	* File Transfer  Protocol, essential for transferring files
	* Some servers may have their own method for transferring files
	* All servers will provide unlimited FTP access and there is no limit on the amount of data that can be transferred
* Scalability
	* An essential feature of hosting a website
	* Scalability refers to the servers ability to modify the features of the site as needed such as increasing storage or bandwidth

After hosting a web server or creating one, the first thing that you will have is a home directory, a place to store files.

### Viewing a Page

If you store a web page in a file called index.html, to view the page you would go to the address <http://domain_name/index.html>. If index.html was not in the home directory but rather in another directory called pages, you would go to the address <http://domain_name/pages/index.html>.
Remember to organize the files into folders and subdirectories so that you can access the files later and will also have an easier time uploading changed files to the host server.
Remember when referencing a file to do so with respect to the root directory. Although index.html may be in C:/xampp/domain\_name/htdocs/pages/index.html, the C:/xampp/htdocs is native to your local computer and will not hold up if referenced elsewhere.

### Transferring Files

Typically, a host server will provide support for a File Transfer Protocol(FTP). To make use of this, you want to use an FTP client which will allow you to navigate through your files, create folder, upload files, and etc. Popular clients for Windows include CuteFTP and CyberDuck. Furthermore, some text editors such as Coda will provide a built-in FTP client to ease the process of creating/editing files and uploading them back to the host server. Servers that run cPanel will also allow you to use cPanel's interface for uploading files and other file related tasks. Finally, web hosts that don't provide FTP support will typically have instructions/guidance in order to allow you to upload site files.

### Updating Files

Web host's not only allow you to add and transfer files over to a remote server, but to update/replace existing files. Say you made an error in a file you uploaded but never noticed. Although you cannot directly go to the web host and fix the error, you can resolve the issue on your local computer and then push the changes over to the host server. Just make sure to get the location of the file right, as you stand to add an unneeded file that might lead to bugs or replace a file that didn't need replacing.
