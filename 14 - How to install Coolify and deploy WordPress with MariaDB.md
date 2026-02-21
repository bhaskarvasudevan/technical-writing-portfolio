# How to install Coolify and deploy WordPress with MariaDB

Coolify is a simple self-hosting platform that helps install applications like WordPress on your own servers with minimal effort. 
This guide walks you through the steps to install Coolify on an Ubuntu server and deploy WordPress with a MariaDB database. 

## Pre-requisites
* A server running Ubuntu 24.04 
* Root access to the server
* A public IP address for the server
* Port 8000 accessible on the server (for Coolify)
* DNS entries (A separate **A** record each for Coolify and WordPress) 

## Note
In this guide, you will see references to my server, DNS domain, and FQDNs in the screenshots. 
I tested the steps on a Ubuntu 24.04 VM. 
You will need to replace these for your setup.  
* 46.62.217.177 is my server's IP address.
* **_bhaskarvasudevan.in_** is my DNS domain.
* https://coolify.bhaskarvasudevan.in is the URL I use for my Coolify setup.
* https://wordpress-mariadb.bhaskarvasudevan.in is the URL I use for my WordPress setup.

## 1. Prepare the Ubuntu server 
1. Log in to your server via SSH as the root user. 
```
ssh root@your-server-IP 
```

2. Update the server. You want the server to be updated with the latest updates and patches before installing Docker and Coolify.
```
sudo apt update && sudo apt upgrade -y 
```

3. Wait for the update to complete. Reboot the server. This is good practice and improves the reliability of subsequent steps. 
```
reboot
``` 

## 2. Install Coolify
1. Log in to your server via SSH as the root user.
```
ssh root@your-server-IP 
```

2. Now, install Coolify using the install script for self-hosting. This step can take a few minutes. 
```
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | sudo bash
```

3. Wait for the installation to complete. The installer will:
   * Install required packages (curl, wget, git, jq, openssl)
   * Install Docker
   * Set up Coolify and helper services as Docker containers
   * Configure the Docker network pool 

![Coolify install completed](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/coolify_install_completed.png)

4. Once completed, you will see a component summary.


## 3. Access the Coolify web interface

1. Open your web browser and navigate to:`
```
http://your-server-IP:8000 
```
2. You will be redirected to the registration page.



## 4. Set up the Coolify admin account
1. Fill in the root user setup form
   * Name: Your full name
   * Email address: Your email address
   * Password: _Min 8 characters with uppercase, lowercase, number, and symbol_
2. Click **Create Account**. 

![Wordpress root user setup](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/coolify_root_user_setup.png)

## 5. Complete the initial setup

### 5.1 Welcome screen
1. Review what will be configured:
   * Server Connection (SSH deployment)
   * Docker Environment (automated setup)
   * Project Structure (resource organization)
2. Click **Let's go!**

![Coolify lets go](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/click_coolify_lets_go.png)

### 5.2 Choose server type
1. Select **This Machine (Quick Start option)** to deploy on the server running Coolify.

![Select this machine](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/select_this_machine_quick_start.png)

### 5.3 Create your first project
1. Click **Create "My First Project"**

   This creates a project with a default production environment to organize your applications.  

![Create my first project](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/create_my_first_project.png)

### 5.4 Setup complete
1. **Verify the configuration** shows: 
   * Server: _localhost (host.docker.internal)_
   * Project: _My first project (Production environment ready)_
   * Docker Engine: _Installed and running_
2. Click **Deploy Your First Resource** or **Go to Dashboard**. Both take you to the dashboard. 

![Deploy your first resource](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/deploy_your_first_resource.png)

### 5.5 Modify settings 
1. Click **Settings** 
2. Enter the complete URL for Coolify (https://<coolify.FQDN>) in the **Domain** field. (e.g., https://coolify.your.domain) 
3. Enter a name in the **Name** field. (e.g., coolify)
4. Click **Save**. 
5. You will see **Success (Instance settings updated successfully!)**. 

![Specify https Coolify URL](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/specify_https_coolify_url_and_name.png)

## 6. Deploy WordPress with MariaDB

### 6.1 Create New Resource
1. Click **Dashboard**.
2. Select **My first project**.
3. Click **+ New Resource**. 

![Add New Resource](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/click_add_resource.png)

### 6.2 Select WordPress template
1. In the search box, type **WordPress**.
2. In the search results, click **WordPress with MariaDB**. 

![Select WordPress with MariaDB](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/select_wordpress_with_mariadb.png)



### 6.3 Configure the service URL 
1. The configuration page will display.
2. Navigate to General -> Services -> WordPress. 
3. Click **Edit** next to the URL. 

![Edit default WordPress URL](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/edit_default_wordpress_url_1.png)

4. In **Edit Domains**, enter the complete URL for WordPress (https://<wordpress.FQDN>). (e.g., https://wordpress.your.domain) 

![Enter WordPress FQDN](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/specify_https_wordpress_url.png)

5. Click **Save** to save the URL. 
6. Click **X** on the top right-hand side to close the dialog.  


## 7. Deploy the service
1. Click the Deploy button in the top-right corner.

![Deploy WordPress MariaDB](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/deploy_wordpress_mariadb.png)

2. A Service Startup modal will appear showing deployment logs:
   * Docker images are being downloaded
   * Layers being extracted
   * Checksums being verified
3. Wait for the deployment to complete. You'll see progress indicators for:
   * WordPress image download
   * MariaDB image download
   * Container startup

![WordPress MariaDB Service Startup](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/wordpress_mariadb_service_startup.png)

## 8. Access your WordPress site
1. Once deployed, the service status will change from "Exited" to "Running".
2. Find your WordPress URL in the Links or the Services section.
3. Open a web browser and navigate to **https://<wordpress.FQDN>** (e.g., https://wordpress.your.domain/)

## 9. Install WordPress
1. Select **English (United States)**.
2. Click **Continue**.

![WordPress language selection](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/wordpress_language_selection.png)

3. Fill in the installation form.
   * Site title: Title for your site. (e.g., myblogsite) 
   * Username: admin username (e.g., **admin**)
   * Password: Click **Hide**. Then enter the password. 
   * Your email: Your email address

![WordPress installation form](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/wordpress_install_form.png)

4. Click **Install WordPress**. 
5. Installation completes. 


## 10. Log on to WordPress
1. Wait for installation to succeed. 

![WordPress installation complete](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/wordpress_install_complete.png)


2. Click **Log In**. 

![WordPress login page](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/wordpress_login_page.png)

3. You are logged in. 

![Logged on to WordPress](https://github.com/bhaskarvasudevan/technical-writing-portfolio/blob/main/images/logged_in_to_wordpress.png)

## 11. Troubleshooting
1. Make sure port 8000 on the server is accessible. 
If not, check firewall settings. 

2. **A** records set up on DNS can take from minutes to hours to propagate. 
To confirm DNS resolution works as expected, run *nslookup* on the server and check if forward and reverse name lookups succeed.

3. The SSL certificates associated with the Coolify URL and WordPress URL are self-signed.
They are not CA-signed. 
If browser warnings prevent you from accessing the URLs, try a different browser, e.g., Firefox, for testing purposes. 









