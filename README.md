# DomainSettingGuide

## How to Connect a Custom Domain to GitHub Pages

Follow these steps to purchase a custom domain and connect it to your GitHub Pages site.

1. **Purchase a Custom Domain**
   - Visit a domain provider to purchase a domain of your choice (e.g., `example.com`).
   - After purchasing, you’ll have access to the domain's settings, including DNS configuration, which will be needed in later steps.

2. **Enable GitHub Pages**
   - Go to the **Settings** tab of your GitHub repository.
   - Select **Pages** from the left menu.
   - Under **Source**, choose the branch you want to deploy (typically `main` or `gh-pages`) and the directory (`/root` or `/docs`).
   - Once selected, GitHub will generate a default URL (`username.github.io/repository-name`) for your site.   

3. **Set Up Your Custom Domain**
   - In the GitHub Pages settings, under **Custom domain**, enter your custom domain (e.g., `www.example.com`) and save.

4. **Configure DNS Settings**
   - Log in to your domain provider (e.g., GoDaddy, Cloudflare) and update the **DNS settings** as follows:
     - Add **A records** pointing to the following GitHub IP addresses:
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`
     - If you’re using a subdomain (e.g., `www.example.com`), add a **CNAME record** pointing to `username.github.io`.

5. **Enable HTTPS (Optional)**
   - After DNS propagation, return to your GitHub Pages settings and enable **Enforce HTTPS** for secure access.

> **Note:** DNS settings may take up to 24 hours to propagate.

Once these steps are complete, your GitHub Pages site should be accessible through your custom domain!
