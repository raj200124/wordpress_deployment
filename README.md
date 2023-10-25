Deploying a WordPress application on an EC2 instance involves several steps. Here's a general guide on how to do it:

**Prerequisites:**
1. An AWS account with an EC2 instance running.
2. A domain name (if you want to access your WordPress site via a custom domain).
3. SSH access to your EC2 instance.

**Step 1: Launch an EC2 Instance:**
   - Log in to your AWS console.
   - Launch an EC2 instance, typically using an Amazon Linux or Ubuntu Server AMI.
   - Configure security groups to allow HTTP (port 80) and HTTPS (port 443) traffic.

**Step 2: Connect to Your EC2 Instance:**
   - Use SSH to connect to your EC2 instance.

**Step 3: Install Required Software:**
   - Update your system: `sudo yum update` or `sudo apt-get update`.
   - Install Apache web server: `sudo yum install httpd` or `sudo apt-get install apache2`.
   - Install PHP: `sudo yum install php` or `sudo apt-get install php`.
   - Install MySQL or MariaDB (a MySQL drop-in replacement): `sudo yum install mariadb-server` or `sudo apt-get install mariadb-server`.

**Step 4: Configure MySQL or MariaDB:**
   - Secure your database server with `mysql_secure_installation`.

**Step 5: Install and Configure WordPress:**
   - Download WordPress: `cd /var/www/html` and `sudo wget https://wordpress.org/latest.tar.gz`.
   - Extract WordPress: `sudo tar -xzvf latest.tar.gz`.
   - Create a database and user in MySQL or MariaDB for WordPress.
   - Configure the WordPress `wp-config.php` file with your database information:
     ```
     cd /var/www/html/wordpress
     sudo mv wp-config-sample.php wp-config.php
     sudo nano wp-config.php
     ```
   - Set the authentication keys and database credentials.

**Step 6: Set File Permissions:**
   - Set proper file permissions: `sudo chown -R apache:apache /var/www/html/wordpress`.
   - Make sure Apache can write to directories like `wp-content/uploads`.

**Step 7: Configure Apache:**
   - Create a virtual host for your WordPress site in Apache.
   - Set your domain or public IP as the `ServerName`.

**Step 8: Start Apache:**
   - Start and enable Apache: `sudo systemctl start httpd` and `sudo systemctl enable httpd`.

**Step 9: Access Your WordPress Site:**
   - Open your web browser and navigate to your EC2 instance's public IP or custom domain.
   - Follow the WordPress setup wizard, provide your database information, and set up your admin account.

**Step 10: Additional Configuration:**
   - For a secure WordPress site, consider installing an SSL certificate.
   - Regularly update WordPress, themes, and plugins.

You've now deployed WordPress on your EC2 instance. This is a basic setup, and you can further enhance it by fine-tuning Apache, securing your instance, and optimizing performance.
