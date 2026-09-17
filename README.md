# MAP Azure Resource Validator — Cloudflare Pages Deployment

This folder is a static website. No build command or server is required.

## Option 1: Cloudflare dashboard upload

1. Create a Cloudflare Pages project using **Direct Upload**.
2. Upload the contents of this folder, including `index.html`.
3. Deploy the site.
4. Open the generated `*.pages.dev` URL and test the validator.

Important: upload the folder contents, not the ZIP file contents as a nested folder. The deployed site must have `index.html` at its top level.

## Option 2: Wrangler CLI

From this folder, run:

```bash
npx wrangler login
npx wrangler pages project create map-azure-validator
npx wrangler pages deploy . --project-name map-azure-validator
```

The site will be available at a URL similar to:

```text
https://map-azure-validator.pages.dev
```

If the project already exists, only run:

```bash
npx wrangler pages deploy . --project-name map-azure-validator
```

## Team-only access with Cloudflare Access

After the Pages site is deployed:

1. Open **Cloudflare Zero Trust**.
2. Go to **Access → Applications**.
3. Add a self-hosted application.
4. Enter the Pages URL, or configure a company-owned hostname.
5. Create an **Allow** policy for the approved company emails, email domain, or Entra ID group.
6. Add a catch-all **Deny** policy if required by your company policy.
7. Test with an approved and an unapproved account.

Recommended policy approach:

- Allow: the team’s approved Microsoft Entra ID group
- Deny: everyone else

## Updating the app

Replace `index.html` with the newer version and deploy again. For frequent updates, connect the Pages project to a Git repository so every approved change can be deployed consistently.

## Privacy note

The validator runs in the browser. It does not call Azure, ServiceNow, or an external database, and it does not intentionally save caller information. Do not paste passwords, client secrets, tokens, or other sensitive credentials into the tool.
