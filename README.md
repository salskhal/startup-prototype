# The Future of AI-Powered Solutions - Startup Web Application

A professionally deployed web application showcasing technical skills through modern cloud infrastructure, reverse proxy configuration, and SSL-secured domain setup.

## 🚀 Live Demo

**Website:** [https://gra8sal.xyz](https://gra8sal.xyz)

![screenshot](/screenshot.png)

## 📋 Project Overview

This project demonstrates a complete web application deployment pipeline featuring:

- Dynamic landing page with interactive elements
- Professional cloud infrastructure setup
- Reverse proxy configuration
- SSL certificate implementation
- Custom domain configuration

## 🏗️ Architecture

```
Internet → DNS (gra8sal.xyz) → AWS EC2 → Nginx (Reverse Proxy) → Node.js App (Port 3000)
```

## 🛠️ Technology Stack

- **Cloud Provider:** AWS EC2
- **Operating System:** Ubuntu 24.04 LTS
- **Web Server:** Nginx (Reverse Proxy)
- **Application:** Node.js
- **SSL Certificate:** Let's Encrypt (Certbot)
- **Domain:** Custom domain (gra8sal.xyz)
- **Frontend:** HTML/CSS/JavaScript with animations

## 📖 Deployment Guide

### Step 1: AWS EC2 Setup

1. **Launch EC2 Instance**

   ```bash
   # Instance Details
   AMI: Ubuntu Server 22.04 LTS
   Instance Type: t2.micro (Free Tier)
   Storage: 8GB GP2
   ```

2. **Configure Security Group**

   ```bash
   # Inbound Rules
   SSH (22): Your IP Address
   HTTP (80): 0.0.0.0/0
   HTTPS (443): 0.0.0.0/0
   ```

3. **Connect to Instance**
   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-ip
   ```

### Step 2: Server Configuration

1. **Update System**

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Node.js**

   ```bash
   curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
   sudo apt-get install -y nodejs
   node --version
   npm --version
   ```

3. **Install Nginx**
   ```bash
   sudo apt install nginx -y
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```

### Step 3: Application Setup

1. **Clone Repository**

   ```bash
   git clone https://github.com/salskhal/startup-prototype.git
   cd startup-web-app
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Start Application**

   ```bash
   # For development
   npm start

   # For production (with PM2)
   npm install -g pm2
   pm2 start app.js
   pm2 startup
   pm2 save
   ```

### Step 4: Nginx Configuration

1. **Create Nginx Configuration**

   ```bash
   sudo nano /etc/nginx/sites-available/default
   ```

2. **Nginx Configuration File**

   ```nginx
   server {

       server_name gra8sal.xyz www.gra8sal.xyz;

       location / {
           proxy_pass http://localhost:3000;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```


### Step 5: Domain Configuration

1. **Purchase Domain**

   - Registered domain: `gra8sal.xyz`

2. **Configure DNS Records**

   ```
   Type: A     Name: @       Value: YOUR_EC2_PUBLIC_IP    TTL: 300
   Type: A     Name: www     Value: YOUR_EC2_PUBLIC_IP    TTL: 300
   ```

3. **Verify DNS Propagation**
   ```bash
   nslookup gra8sal.xyz
   dig gra8sal.xyz
   ```

### Step 6: SSL Certificate Setup

1. **Install Certbot**

   ```bash
   sudo apt install certbot python3-certbot-nginx -y
   ```

2. **Obtain SSL Certificate**

   ```bash
   sudo certbot --nginx -d gra8sal.xyz -d www.gra8sal.xyz
   ```



## 🔧 Application Features

### Landing Page Components

- **Hero Section:** Professional introduction and role
- **Our Innovation:** Clear innovation value
- **Professional Bio:** Skills, experience, and education
- **Interactive Elements:** CSS animations and hover effects
- **Responsive Design:** Mobile-friendly layout

### Technical Features

- **Reverse Proxy:** Nginx handling requests to Node.js backend
- **SSL Security:** HTTPS encryption with Let's Encrypt
- **Process Management:** PM2 for application lifecycle


## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name** - Lead Cloud Engineer

- Website: [https://gra8sal.xyz](https://gra8sal.xyz)
- GitHub: [salskhal](https://github.com/salskhal)
- LinkedIn: [salskhal](https://linkedin.com/in/salskhal)

## 🙏 Acknowledgments

- AWS for reliable cloud infrastructure
- Let's Encrypt for free SSL certificates
- Nginx for powerful reverse proxy capabilities
- The open-source community for excellent tools and documentation

---

**Project Status:** ✅ Production Ready
