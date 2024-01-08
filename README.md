## Custom Error Pages Setup for Nginx-Proxy-Manager (NPM)

### Step 1: Create Folders and File

Create the necessary folders and file structure if not already present.


```bash
mkdir -p /data/nginx/custom
mkdir -p /data/nginx/error_pages
touch /data/nginx/custom/server_proxy.conf
```

### Step 2: Edit server_proxy.conf

Edit the `server_proxy.conf` file placed in the `/data/nginx/custom` folder. You can use a text editor like nano or vi.


```bash
nano /data/nginx/custom/server_proxy.conf
```

Add the following configuration to `server_proxy.conf`:

```nginx
error_page 400 /error_pages/400.html;
error_page 401 /error_pages/401.html;
error_page 402 /error_pages/401.html;
error_page 403 /error_pages/403.html;
error_page 404 /error_pages/404.html;
error_page 405 /error_pages/405.html;
error_page 407 /error_pages/407.html;
error_page 408 /error_pages/408.html;
error_page 409 /error_pages/409.html;
error_page 410 /error_pages/410.html;
error_page 411 /error_pages/411.html;
error_page 412 /error_pages/412.html;
error_page 413 /error_pages/413.html;
error_page 416 /error_pages/416.html;
error_page 418 /error_pages/418.html;
error_page 429 /error_pages/429.html;
error_page 500 /error_pages/500.html;
error_page 501 /error_pages/501.html;
error_page 502 /error_pages/502.html;
error_page 503 /error_pages/503.html;
error_page 504 /error_pages/504.html;
error_page 505 /error_pages/505.html;
proxy_intercept_errors on;

location /error_pages/ {
    alias /data/nginx/error_pages/;
    internal;
}

```

### Step 3: Copy Custom Error HTML Pages

Copy your favorite custom error HTML pages to the `/data/nginx/error_pages/` folder.

### Step 4: Restart Nginx-Proxy-Manager (NPM) Docker Container

After completing the configuration, restart your Nginx-Proxy-Manager docker container to apply the changes.

### Step 5: Test

Test if the new globally set error pages are working by intentionally triggering errors (e.g., accessing a non-existing page) and checking if the custom error pages are displayed.

This setup allows you to have globally configured custom error pages for a more user-friendly and informative experience. Customize the HTML pages according to your preferences.
