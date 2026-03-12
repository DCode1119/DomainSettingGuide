# DomainSettingGuide

## How to Connect a Custom Domain to GitHub Pages

Follow these steps to purchase a custom domain and connect it to your GitHub Pages site safely.

1. **Purchase a Custom Domain**
   - Buy a domain from a domain provider such as GoDaddy, Namecheap, or Cloudflare.
   - After purchasing the domain, make sure you can access the provider's DNS settings because you will need them later.

2. **Enable GitHub Pages**
   - Open your GitHub repository.
   - Go to **Settings** > **Pages**.
   - Under **Build and deployment**, choose the branch you want to publish, usually `main` or `gh-pages`, and select the folder to deploy.
   - GitHub will generate a default Pages URL such as `username.github.io/repository-name`.

3. **Add Your Custom Domain in GitHub First**
   - In the GitHub Pages settings, enter your custom domain under **Custom domain** and save it.
   - Do this before updating DNS records at your domain provider. Adding DNS records first can create a domain takeover risk.

4. **Verify the Domain (Recommended)**
   - Verify your custom domain with GitHub before or during setup if the option is available for your account.
   - Domain verification helps prevent other users from claiming your domain if your Pages site is disabled or your repository changes later.

5. **Configure DNS Settings**
   - Log in to your domain provider and update the DNS records based on the type of domain you want to use.
   - **For an apex domain** such as `example.com`:
     - Add these four **A records**:
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`
     - If your DNS provider supports it, you can also use `ALIAS` or `ANAME` records instead of manually managing apex `A` records.
     - You may also add GitHub Pages `AAAA` records if you want IPv6 support.
   - **For a subdomain** such as `www.example.com` or `blog.example.com`:
     - Add a **CNAME record** pointing to `username.github.io`.
   - If you want both the apex domain and the `www` subdomain to work, it is a good idea to configure both so redirects work cleanly.

6. **Avoid Unsafe DNS Configurations**
   - Do not use wildcard DNS records such as `*.example.com` for GitHub Pages unless you fully understand the security implications.
   - If you stop using GitHub Pages, remove the related DNS records so the domain does not remain exposed to takeover issues.

7. **Wait for DNS Propagation**
   - DNS changes may take up to 24 hours to propagate, although they often update sooner.
   - During this period, your custom domain may work inconsistently depending on DNS caching.

8. **Enable HTTPS**
   - After GitHub detects the correct DNS records and finishes certificate provisioning, enable **Enforce HTTPS** in the Pages settings.
   - This option may take some time to appear after the DNS records are configured correctly, so do not expect HTTPS to become available immediately.

## Quick DNS Summary

- **Apex domain**: use `A` records, and optionally `ALIAS` or `ANAME` if your provider supports them.
- **Subdomain**: use a `CNAME` record that points to `username.github.io`.
- **Recommended setup if you want both hostnames**: configure both `example.com` and `www.example.com` for better compatibility and redirects.

## Important Notes

- DNS propagation can take up to 24 hours.
- HTTPS should be enabled as soon as GitHub makes it available.
- Keep the GitHub Pages custom domain setting and the DNS records aligned.
- If your site is disabled or deleted, remove stale DNS records to reduce takeover risk.

Once these steps are complete, your GitHub Pages site should be available through your custom domain.
