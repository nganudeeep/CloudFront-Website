# Static Website on AWS S3 + CloudFront

This project shows how I hosted a simple static website on Amazon S3 and delivered it globally through Amazon CloudFront with HTTPS. I learned how S3 static hosting works, how CloudFront handles caching, and how to fix common AWS configuration issues.

Live Website: https://d14ymxlnl9e1app.cloudfront.net/(Deleted)

## What This Project Uses
- Amazon S3 (static website hosting)
- CloudFront (global CDN + HTTPS)
- S3 bucket policies
- HTTP → HTTPS redirection
- CloudFront cache invalidation

---

## Steps I Followed
1. Created an `index.html` file locally.
2. Created an S3 bucket and uploaded the file.
3. Enabled Static Website Hosting in the bucket.
4. Created a CloudFront distribution and selected the S3 Website Endpoint as the origin.
5. Set the default root object to `index.html`.
6. Disabled caching for faster updates.
7. Fixed 403 AccessDenied issues.
8. Created CloudFront invalidations when updating the site.

---

## Troubleshooting I Solved

### 1. 403 AccessDenied
- Caused by Block Public Access and missing bucket policy.
- Fixed by turning off Block Public Access (beginner mode) and adding a public-read policy.

### 2. Wrong Origin Selected
- The REST endpoint does not work for beginner setup.
- Fixed by choosing the S3 Website Endpoint (`s3-website-region.amazonaws.com`).

### 3. Default Root Object Missing
- CloudFront returned 403 without a root file.
- Fixed by setting `index.html` in the distribution settings.

### 4. CDN Cache Not Updating
- CloudFront served older cached versions.
- Fixed using `CachingDisabled` and invalidations (`/*`).

---

## What I Learned
- How S3 static hosting works internally.
- How CloudFront connects to S3.
- How HTTPS is handled by CloudFront.
- How to debug 403 errors.
- How CDN caching works.
- How to refresh content using invalidations.

---

## Future Improvements
- Make the S3 bucket private using OAC (Origin Access Control).
- Add GitHub Actions for CI/CD.
- Add a custom domain with Route 53 + ACM.
- Add a small backend using Lambda + API Gateway.

---

## Project Status
Working and fully deployed with HTTPS and CloudFront CDN.
