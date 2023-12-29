![Alt text](image.png)


What is Apache HTTP Server and How to Install? Adjusting the Firewall + Checking your Web Server + Managing the Apache Process

The Apache HTTP Server, commonly referred to as Apache, is an open-source web server software developed and maintained by the Apache Software Foundation. It is one of the most widely used web servers globally. The Apache web server plays a crucial role in serving static and dynamic content over the World Wide Web.

Key features of the Apache web server include:

1. **Open Source:** Apache is open-source software, which means its source code is freely available to the public. This encourages collaboration, allows users to modify the code, and promotes a community-driven development model.

2. **Cross-Platform:** Apache is designed to work on various operating systems, including Unix, Linux, Windows, and more. This cross-platform compatibility makes it versatile and widely applicable.

3. **Module Support:** Apache's modular architecture allows users to extend its functionality by adding modules. These modules can provide additional features such as authentication mechanisms, URL rewriting, and support for various programming languages.

4. **Security:** Apache includes features for securing web servers, including support for SSL/TLS for encrypted communication, access control mechanisms, and various security modules.

5. **Performance:** Apache is known for its performance and scalability. It can handle a large number of concurrent connections and efficiently serve static and dynamic content.

6. **Configuration:** Apache's configuration files are flexible and allow administrators to customize the server settings based on their specific needs. The configuration files use a simple and human-readable syntax.

7. **Community Support:** As an open-source project, Apache benefits from a large and active community of developers and users. This community provides support, documentation, and contributes to the ongoing development of the software.

Apache is commonly used in conjunction with other software components, such as the PHP scripting language and the MySQL or PostgreSQL databases, to create a full web application stack. The combination of Apache, along with these technologies, is often referred to as the LAMP (Linux, Apache, MySQL/MariaDB, PHP/Perl/Python) stack.


**********
Apache Web Server Installation on Ubuntu 22.04 LTS (Desktop/Server) >> PC/VB/VM/Azure/AWS/GCP/... >>

Update Package Lists
```bash
sudo apt update -y
```

Install Apache
```bash
sudo apt install apache2 -y
```

If you want to, you can also install the Apache documentation and some Apache utilities. You’ll need the Apache utilities for some of the modules we’ll install later.
```bash
sudo apt-get install apache2-doc apache2-utils -y
```

Start Apache
After the installation is complete, Apache should start automatically. If it doesn't, you can start it manually with:
```bash
sudo systemctl start apache2
```

Enable Apache to Start on Boot
To ensure Apache starts automatically when your system boots up, run:
```bash
sudo systemctl enable apache2
```

Check Apache Status
You can check the status to ensure Apache is running without any issues:
```bash
sudo systemctl status apache2
```

Adjust Firewall Settings (if needed):
If you are running a firewall (e.g., UFW), you might need to allow traffic to the Apache service. You can enable the default Apache profile for UFW:
```bash
sudo ufw allow 'Apache'
```

Allow incoming SSH connections by adding a rule to the UFW configuration:
```bash
sudo ufw allow ssh
```

If UFW is not installed, you can install it and enable it with:
```bash
sudo apt install ufw -y
sudo ufw enable
```

After enabling UFW, you may want to check the status:
```bash
sudo ufw status
```

After making changes, reload UFW for the new rules to take effect:
```bash
sudo ufw reload
```
      
List the ufw application profiles by running the following:
```bash
sudo ufw app list
```

Access Apache Default Page
Open a web browser and navigate to `http://your_server_IP` or `http://localhost`. You should see the default Apache welcome page, indicating that Apache is successfully installed.
You can access the default Apache landing page to confirm that the software is running properly through your IP address. If you do not know your server’s IP address, you can get it a few different ways from the command line.
Try writing the following at your server’s command prompt:
```bash
hostname -I
```

Another option is to use the free icanhazip.com tool. This is a website that, when accessed, returns your machine’s public IP address as read from another location on the internet:
```bash
curl -4 icanhazip.com
```

To stop your web server, run:
```bash
sudo systemctl stop apache2
```

To stop and then start the service again, run:
```bash
sudo systemctl restart apache2
```

If you are simply making configuration changes, Apache can often reload without dropping connections. To do this, use the following command:
```bash
sudo systemctl reload apache2
```

By default, Apache is configured to start automatically when the server boots. If this is not what you want, disable this behavior by running:
```bash
sudo systemctl disable apache2
```
