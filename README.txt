SETTING UP katealtemuscullen.org ON GITHUB PAGES (domain bought from Cloudflare)

What's in this folder
  index.html   Your whole site (one page). Edit the text in [square brackets].
  style.css    Colors and fonts (set at the top of the file).
  img/         Put a square photo here named photo.jpg
  cv/          Put your CV here named cv.pdf
  CNAME        Already contains katealtemuscullen.org. Leave it as is.
  .nojekyll    Hidden helper file; tells GitHub to publish the files exactly as they are.
               (Your computer may hide it. If it doesn't upload, that's fine.)

PART 1: PUT THE SITE ON GITHUB
1. Sign in to github.com. Click "+" (top right) > "New repository".
2. Repository name: YOURUSERNAME.github.io  (your exact GitHub username).
   Choose Public. Click "Create repository".
3. On the next page click "uploading an existing file". Drag in everything
   in this folder (index.html, style.css, CNAME, and the img and cv folders).
   Click "Commit changes".
4. Go to Settings > Pages. Under "Build and deployment", set Source to
   "Deploy from a branch", Branch to "main" and folder "/ (root)". Click Save.
5. Wait 1-2 minutes, then visit https://YOURUSERNAME.github.io to check it works.

PART 2: POINT THE DOMAIN AT GITHUB (in Cloudflare)
6. Sign in to dash.cloudflare.com. Click katealtemuscullen.org, then DNS > Records.
7. Delete any existing A, AAAA or CNAME records for "katealtemuscullen.org"
   or "www" (Cloudflare sometimes adds placeholders). Do NOT add any "*" (wildcard) record.
8. Add four A records. For each: Type = A, Name = @, IPv4 address = one of:
      185.199.108.153
      185.199.109.153
      185.199.110.153
      185.199.111.153
   IMPORTANT: click the orange cloud so it turns GREY ("DNS only") on every record.
9. Add one CNAME record: Type = CNAME, Name = www,
   Target = YOURUSERNAME.github.io   Proxy status: DNS only (grey cloud).
   (Optional: also add AAAA records for @ pointing to 2606:50c0:8000::153,
   2606:50c0:8001::153, 2606:50c0:8002::153 and 2606:50c0:8003::153, grey cloud.)

PART 3: CONNECT AND SECURE
10. Back on GitHub: repository Settings > Pages > Custom domain.
    Type katealtemuscullen.org and click Save. Wait for "DNS check successful"
    (minutes to a few hours).
11. When it's available, tick "Enforce HTTPS". This can take up to 24 hours to appear.
12. Visit https://katealtemuscullen.org and https://www.katealtemuscullen.org.
    Both should show your site.

PART 4: PROTECT THE DOMAIN (10 minutes, do it once)
13. GitHub: click your profile photo > Settings > Pages (left menu) > "Add a domain".
    Enter katealtemuscullen.org. GitHub shows a TXT record.
14. Cloudflare: DNS > Records > Add record. Type = TXT, and copy the Name and
    Content exactly as GitHub shows them. Save, then click "Verify" on GitHub.
    This stops anyone else from ever attaching your domain to their GitHub site.
15. Cloudflare: Domain Registration > Manage Domains > katealtemuscullen.org.
    Make sure Auto-renew is on.
16. Turn on two-factor authentication for both your GitHub and Cloudflare accounts.

EDITING LATER
- On github.com, click index.html, then the pencil icon. Edit, then "Commit changes".
  The site updates in about a minute.
- To replace the photo or CV, open the img or cv folder > "Add file" > "Upload files",
  using the same file name (photo.jpg / cv.pdf).

IF SOMETHING GOES WRONG
- "Enforce HTTPS" unavailable or certificate errors: almost always an orange cloud
  in Cloudflare. Make every record grey (DNS only) and wait.
- Too many redirects: same cause; also check Cloudflare SSL/TLS is not "Flexible".
- Custom domain box keeps emptying: make sure the CNAME file is still in the repository.
