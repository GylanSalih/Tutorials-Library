# Overview VPS Setup for Next.js (React) Application

### This guide walks you through the steps to set up a Next.js project on an Ubuntu VPS. The steps include:

1. **Preparing the VPS**: Installing necessary dependencies (Node.js, PM2, Git) and setting up the development environment.
2. **Cloning the Project**: Downloading the Git repository and installing dependencies for the Next.js project.
3. **Starting the Application**: Running the Next.js project using PM2 for process management.
4. **Creating SSL Certificate Using Certbot**: Setting up SSL certificates for your custom domain using Certbot (Let's Encrypt).
5. **Optional Apache Reverse Proxy Configuration**: Setting up Apache to serve the Next.js project via a custom domain.
6. **Automating Updates with Cron**: Automatically fetching Git updates and restarting the application at regular intervals.
7. **GitHub Webhook (Optional)**: Setting up a GitHub webhook to automatically update the repository when changes occur.
8. **Manual Updates**: Steps for manually pulling repository updates and restarting the application.

### Prerequisites

- A VPS with Ubuntu 24
- Node.js (at least version 18.x)
- PM2 for process management
- Apache as a Reverse Proxy (optional, if you want to use a custom domain)
- Git for version control
- `npm` (or `yarn`)
- Certbot for SSL certificate generation (if using HTTPS)

# Step-by-Step Guide

<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 1. Preparing the VP</summary>

  - **Update and Install Dependencies:**
  
    ```bash
    sudo apt update && sudo apt upgrade -y
    sudo apt install git curl build-essential
    ```

  - **Install Node.js (npm is installed automatically with Node.js):**
  
    To install Node.js (the best way is using `nvm`):
  
    ```bash
    curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    sudo apt install -y nodejs
    ```

  - **Install PM2:**
  
    ```bash
    sudo npm install -g pm2
    ```

  - **Install Git:**
  
    ```bash
    sudo apt install git
    ```

</details>


<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 2. Clone the Project and Install Dependencies</summary>


- **Clone the Git Repository:**
  ```bash
  git clone https://github.com/yourusername/yourrepo.git /var/www/NextJS-Portify
  ```

- **Navigate to the project directory:**
  ```bash
  cd /var/www/NextJS-Portify
  ```

- **Install the dependencies:**
  ```bash
  npm install
  ```
</details>

<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 3. Start the Next.js Application
</h2></summary>

- **Start with PM2:**
  ```bash
  pm2 start npm --name "nextjs-app" -- run dev
  ```

- **Save PM2 processes (so they restart after a reboot):**
  ```bash
  pm2 save
  ```

</details>



<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 4. Clone the Project and Install Dependencies</h2></summary>

- **Clone your Git repository**:
  
  ```bash
  git clone https://github.com/GylanSalih/NextJS-Portify.git
  cd NextJS-Portify
  ```

- **Install dependencies**:
  
  ```bash
  npm install
  ```

</details>






<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 5. Create SSL Certificate Using Certbot (Let's Encrypt)</h2></summary>

To create an SSL certificate for your domain using Certbot, follow these steps:

1. **Install Certbot and Apache Plugin**:

   ```bash
   sudo apt update
   sudo apt install certbot python3-certbot-apache
   ```

2. **Generate SSL Certificate**:
   - Run Certbot to automatically configure Apache with SSL for your domain:
   
   ```bash
   sudo certbot --apache -d yourdomain.com -d www.yourdomain.com
   ```

   - Certbot will:
     - Automatically configure Apache to use SSL.
     - Request a certificate from Let's Encrypt for `yourdomain.com` and `www.yourdomain.com`.
     - Automatically configure your Apache server for HTTPS.

3. **Test Automatic Renewal**:
   Certbot sets up automatic certificate renewal by default, but you can test it by running:

   ```bash
   sudo certbot renew --dry-run
   ```

   This will simulate the renewal process without actually renewing the certificate. If this command runs without errors, your renewal setup is working.

4. **Check SSL Certificate Expiration**:
   - The SSL certificate from Let's Encrypt is valid for 90 days. To check the expiration date:
   
   ```bash
   sudo certbot certificates
   ```

   - It will show the expiration date of your certificates. Keep in mind that Certbot will automatically renew the certificates if the renewal process is set up correctly.

5. **Configure Apache for SSL**:
   After generating the SSL certificate, Certbot automatically updates your Apache configuration for HTTPS. However, you may need to manually tweak the `000-default-le-ssl.conf` configuration file if any customizations are required.

6. **Set Up Automatic Renewal (If Needed)**:
   If Certbot didn't automatically set up a cron job or systemd timer for certificate renewal, you can set it up manually by adding a cron job to renew the certificate periodically.

   To edit the cron job:
   
   ```bash
   sudo crontab -e
   ```

   Add the following line to renew the certificates twice a day:
   
   ```bash
   0 12 * * * certbot renew --quiet && systemctl reload apache2
   ```

   This ensures that the certificate is automatically renewed without any manual intervention.

</details>




<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 6. Configure Apache as a Reverse Proxy (Optional)</h2></summary>

- **Install Apache:**

  ```bash
  sudo apt install apache2
  ```

- **Enable Apache Modules:**

  ```bash
  sudo a2enmod proxy
  sudo a2enmod proxy_http
  sudo a2enmod ssl
  ```

- **Create an Apache site configuration:**

  ```bash
  sudo nano /etc/apache2/sites-available/000-default.conf
  ```

  Example configuration:

  ```apache
  <VirtualHost *:80>
      ServerName www.yourdomain.com
      DocumentRoot /var/www/NextJS-Portify

      ProxyPass / http://localhost:3001/
      ProxyPassReverse / http://localhost:3001/

      RewriteEngine On
      RewriteCond %{SERVER_NAME} =www.yourdomain.com
      RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
  </VirtualHost>

  <VirtualHost *:443>
      ServerName www.yourdomain.com
      DocumentRoot /var/www/NextJS-Portify

      ProxyPass / http://localhost:3001/
      ProxyPassReverse / http://localhost:3001/

      SSLEngine on
      SSLCertificateFile /path/to/certificate.crt
      SSLCertificateKeyFile /path/to/private.key
  </VirtualHost>
  ```

  ```bash
  sudo nano /etc/apache2/sites-available/000-default-le-ssl.conf
  ```

  Example configuration:

  ```apache
  <IfModule mod_ssl.c>
  <VirtualHost *:443>
    # Replace with your actual domain
    # ServerName and ServerAlias
    ServerName yourdomain.com
    ServerAlias www.yourdomain.com

    # Replace with your Next.js app's directory
    # DocumentRoot
    DocumentRoot /var/www/NextJS-Portify

    # Use the correct paths for your SSL certificate and private key
    # SSL configuration
    SSLEngine on
    SSLCertificateFile /etc/letsencrypt/live/yourdomain.com/fullchain.pem  # Certificate path
    SSLCertificateKeyFile /etc/letsencrypt/live/yourdomain.com/privkey.pem  # Private key path
    Include /etc/letsencrypt/options-ssl-apache.conf  # SSL config from Let's Encrypt

    # Proxy requests to your Next.js app running on port 3001
    # Reverse Proxy
    ProxyPass / http://127.0.0.1:3001/
    ProxyPassReverse / http://127.0.0.1:3001/

    # Logs for errors and access
    # Error and access logs
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
</IfModule>
  ```


- **Enable the site and restart Apache:**

  ```bash
  sudo a2ensite yourdomain.com.conf
  sudo systemctl restart apache2
  ```

</details>


<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 7. Automate Updates with Cron (Optional)</h2></summary>

To ensure that the Git repository is automatically updated, you can set up a cron job to run `git pull` every 10 minutes:

```bash
crontab -e
```

Add the following line to update every 10 minutes:

```bash
*/10 * * * * cd /var/www/NextJS-Portify && git pull origin main && pm2 restart nextjs-app
```

</details>


<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 8. GitHub Webhook (Optional)</summary>

If you'd like to use GitHub webhooks to automatically update the repository, you need to set up an Express server to listen for `POST` requests.

- Create a `webhook-server.js` file with the following content:

  ```javascript
  const express = require('express');
  const exec = require('child_process').exec;

  const app = express();
  app.use(express.json());

  app.post('/deploy', (req, res) => {
      exec('cd /var/www/NextJS-Portify && git pull origin main && pm2 restart nextjs-app', (err, stdout, stderr) => {
          if (err) {
              res.status(500).send('Error: ' + err);
              return;
          }
          res.send('Deploy successful');
      });
  });

  app.listen(8080, () => {
      console.log('Webhook server running on http://localhost:8080');
  });
  ```

- Start the webhook server:

  ```bash
  node webhook-server.js
  ```

- **Allow the port in the firewall (if enabled):**

  ```bash
  sudo ufw allow 8080
  ```

- **Configure the webhook in GitHub:**

  - Add the URL of your webhook server (`http://your-server-ip:8080/deploy`) in the Webhook settings on GitHub.
</details>


<details>
  <summary><h2><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Pushpin.png" alt="Pushpin" width="25" height="25" /> 9. Manually Update the Repository</h2></summary>

If you want to manually update the repository, follow these steps:

1. **Navigate to the project directory:**

   ```bash
   cd /var/www/NextJS-Portify
   ```

2. **Run `git pull` to fetch the latest changes:**

   ```bash
   git pull origin main
   ```

3. **Install dependencies if needed:**

   ```bash
   npm install
   ```

4. **Restart the application:**

   ```bash
   pm2 restart nextjs-app
   ```
</details>
