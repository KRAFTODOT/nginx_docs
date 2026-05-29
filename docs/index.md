# Nginx Proxy Manager: Your Easy-to-Use Reverse Proxy

Nginx Proxy Manager (NPM) is a web UI that allows you to easily configure Nginx as a reverse proxy. It's a fantastic tool for deploying self-hosted applications (like Plex, Nextcloud, Home Assistant, etc.) behind a single public IP address, providing HTTPS encryption, and managing access.  This guide will help you get started.

## 1. What is Nginx Proxy Manager?

* **Reverse Proxy:** Think of it as a gatekeeper. Users connect to NPM, and NPM forwards requests to your internal applications. This hides your internal network from the outside world.
* **HTTPS:** NPM automatically handles SSL/TLS certificates (Let's Encrypt integration!) so you don't have to.
* **Web UI:**  A simple, graphical interface to manage your proxies.
* **Nginx Under the Hood:** NPM uses Nginx, a powerful and widely used web server, to do the actual proxying. You don't need to know Nginx configuration syntax directly, although understanding it can be helpful for advanced use.

## 2. Creating a Proxy Host (Basic Usage)

1. **Login:** Log into the Nginx Proxy Manager web UI using the password you got from Tymon.
2. **Go to "Proxy Hosts":** Click the "Proxy Hosts" tab.
3. **Click "Add Proxy Host":**  This will open a form.
4. **Fill in the Details:**
   * **Domain Names:** Enter the domain or subdomain you want to use to access your application (e.g., `app.it3.iktim.no`).
   * **Scheme:**  `http` (since your internal server is likely using HTTP)
   * **Forward Hostname / IP:** `10.0.0.***` (that's our house's IP range)
   * **Forward Port:** f.e. `80`
   * **Access List:** Use `Local`, so people from Chine will not be able to connect.
   * **Cache Assets:**  (Optional)  Enable if you want NPM to cache static assets.
   * **Block Common Exploits:**  (Recommended) Enable for extra security.
   * **Websockets Support:**  (Optional) Enable if you are going to use APIs.
5. **Click "Save":**

Now, you should be able to access your application by visiting `http://app.it3.iktim.no/` in your web browser. NPM will automatically handle the SSL/TLS certificate (if you have a valid DNS record).

## 3. Common Configurations & Tips

* **Subdomains:**  Create subdomains in your DNS settings (e.g., `app.it3.iktim.no`) and point them to the public IP address of your server.
* **Let's Encrypt Errors:**  If you have trouble obtaining SSL certificates, make sure your domain name is correctly pointed to your server's IP address and that you don't have any DNS propagation delays.  Check the NPM logs in the web UI for more details.
* **Accessing Internal Services via IP Address:**  You can use the internal IP address of your services directly in the "Forward Hostname / IP" field.

## 4. Troubleshooting

* **Check the Logs:**  The NPM web UI provides access to container logs, which can be invaluable for troubleshooting.
* **DNS Propagation:**  Ensure your DNS changes have propagated.  Use a DNS checker tool (like [https://dnschecker.org/](https://dnschecker.org/)) to verify.
* **Firewall:** Make sure your firewall allows traffic on ports 80 and 443.
* **Community Support:** The JC21 Nginx Proxy Manager GitHub repository ([https://github.com/jc21/nginx-proxy-manager](https://github.com/jc21/nginx-proxy-manager)) and community forums are great resources for getting help.



This documentation provides a comprehensive starting point for using our Nginx Proxy Manager. Good luck! Remember to consult the official documentation and community resources for more advanced features and troubleshooting.