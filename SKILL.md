---
name: tiiny-host
description: >
  Publish files to the web instantly. Use when asked to "publish this",
  "host this", "deploy this", "share this on the web", "make a website", or
  "put this online". Outputs a live URL at {subdomain}.tiiny.site.
---

# tiiny.host

**Skill version: 1.0.0**

Publish any file or folder to the web and get a live URL back. Static hosting only.

## Requirements

- Required binaries: `curl`
- Optional environment variable: `$TIINYHOST_API_KEY`, `$TIINYHOST_EMAIL`

## Upload

**Endpoint:** `POST https://ext.tiiny.host/v1/upload`  
**Headers:** `x-email` and/or `x-api-key`  
**Body:** form-data with `files` (file attachments) and optional `domain`.

Example (anonymous upload with email):

```bash
curl -sS -X POST https://ext.tiiny.host/v1/upload \
  -H "x-email: user@example.org" \
  -F "files=@index.html" \
  -F "files=@style.css"
```

Example (permanent upload with API key):

```bash
curl -sS -X POST https://ext.tiiny.host/v1/upload \
  -H "x-api-key: YOUR_API_KEY" \
  -F "files=@index.html" \
  -F "domain=mysite.tiiny.site"
```

When uploading, if the user does not have an API key, they must provide an email to use in the X-Email header, and it creates an **anonymous upload** linked to that email which expires in 1 hour. This only works for emails that aren't already linked to a Tiiny account. With a provided API key, the X-Email is no longer needed and the publish is permanent. The usual flow is to ask for an email from people who have never used tiiny before so they can immediately publish, but then to ask them to generate an api key later to make it permanent.

**File structure:** For HTML sites, place `index.html` at the root of the directory you publish, not inside a subdirectory. The directory's contents become the site root. For example, publish `my-site/` where `my-site/index.html` exists — don't publish a parent folder that contains `my-site/`.

You can also publish raw files without any HTML. Single files get a rich auto-viewer (images, PDF, video, audio). Multiple files get an auto-generated directory listing with folder navigation and an image gallery.

## Update an existing site

**Endpoint:** `PUT https://ext.tiiny.host/v1/upload`  
**Headers:** `x-api-key` (required)  
**Body:** form-data with `files` and `domain` (the existing site’s domain to update).

Example:

```bash
curl -sS -X PUT https://ext.tiiny.host/v1/upload \
  -H "x-api-key: YOUR_API_KEY" \
  -F "files=@index.html" \
  -F "files=@style.css" \
  -F "domain=mysite.tiiny.site"
```

Updates require a saved API key and cannot be used without one.

## API key storage

When calling the APIs, read the API key from these sources (first match wins):

1. `$TIINYHOST_API_KEY` environment variable

## Getting an API key

To upgrade from anonymous upload (24h) to permanent publishing:

1. If you don't already have an email for the user, then ask for one.
2. Request a one-time sign-in code (POST) using the email you have from the user:

```bash
curl -sS -X POST https://ext.tiiny.host/v1/otp/request \
  -H "x-email: user@example.org"
```

3. Tell the user: "Check your inbox for a sign-in code from Tiiny Host and paste it here."
4. Verify the code and get the API key (POST):

```bash
curl -sS -X POST https://ext.tiiny.host/v1/otp/verify \
  -H "x-email: user@example.org" \
  -H "content-type: application/json" \
  -d '{"otp":"123456"}'
```

5. Save the returned `apiKey`.


## Handling specific cases

- If a user asks to publish a site, first ask for their email and use this to upload
- If you get an 'Account already exists' error, push them through the 'Getting an API key' flow so you can save with their API key
- If you get an error which implies a limit has been exceeded, offer the option to replace their existing site, or suggest that the user goes to https://tiiny.host and logs in with their email to upgrade their account to be able to add more sites.

