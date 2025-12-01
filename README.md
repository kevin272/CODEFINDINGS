# FRONTEND UPDATE FOR VPS WORKFLOW

### 1. Clear old frontend files
```bash
rm -rf /var/www/momscharcoalgrill/frontend/*
```

### 2. Deploy new build via SCP
```bash
scp -r ./dist/* name@ip:/var/www/momscharcoalgrill/frontend
```

### 3. Certificate management
```bash
sudo certbot delete
```

### 4. Test and reload Nginx
```bash
sudo nginx -t
sudo systemctl reload nginx
```

### 5. Re‑issue SSL certificate
```bash
sudo certbot --nginx -d mumscharcoalandgrill.com.au -d www.mumscharcoalandgrill.com.au
```

### 6. Adjust ownership and permissions
```bash
cd /var/www/momscharcoalgrill
sudo chown -R www-data:www-data frontend
sudo find frontend -type d -exec chmod 755 {} \;
sudo find frontend -type f -exec chmod 644 {} \;
```

### 7. Final Nginx validation and reload
```bash
sudo nginx -t
sudo systemctl reload nginx
```
