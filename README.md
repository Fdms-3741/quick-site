# HTTPS Server with Traefik and Let's Encrypt

This Docker Compose setup provides an HTTPS web server with automatic SSL certificate management using Traefik and Let's Encrypt.

## Quick Start

1. **Configure your domain:**
   ```bash
   cp .env.example .env
   # Edit .env and set your domain and email
   ```

2. **Update Traefik configuration:**
   - Edit `traefik/traefik.yml` and replace `your-email@example.com` with your actual email

3. **Start the services:**
   ```bash
   docker-compose up -d
   ```

4. **Add your website content:**
   - Place your HTML, CSS, JS files in the `www/` directory
   - The `www/` directory is mounted to the nginx container

## Services

- **Traefik**: Reverse proxy with automatic HTTPS (ports 80, 443, 8080)
- **Web Server**: Nginx serving content from `./www` directory

## Accessing Services

- **Your website**: `https://yourdomain.com`
- **Traefik dashboard**: `http://localhost:8080` (localhost only for security)

## Directory Structure

```
.
├── docker-compose.yml
├── .env
├── traefik/
│   └── traefik.yml
├── www/
│   └── index.html
├── nginx/
│   └── default.conf
└── letsencrypt/
    └── (certificates stored here)
```

## Important Notes

- Ensure your domain points to your server's IP address
- Let's Encrypt requires your server to be accessible from the internet
- Certificates are automatically renewed by Traefik
- The `letsencrypt/` directory persists certificate data

## Customization

- **Web content**: Add files to `www/` directory
- **Nginx config**: Modify `nginx/default.conf`
- **Traefik config**: Modify `traefik/traefik.yml`