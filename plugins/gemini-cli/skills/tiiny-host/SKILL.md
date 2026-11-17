---
name: tiiny-host
description: Publish files or pages made in the conversation as live websites on Tiiny Host, and manage the user's existing Tiiny Host sites. Use when the user asks to publish, host, deploy or share something on the web, or to list, update or delete their Tiiny Host sites.
---

# Publish with Tiiny Host

1. Before publishing, confirm that the user wants the content to be public: anyone with the link can open it.
2. Publish one file per call with `publish_site`. Send text files (HTML, CSS, JS, Markdown) as `fileContent` and binary files (PDF, PNG, JPG, ZIP, DOCX) as `fileContentBase64`. A multi-page static site goes as one ZIP. Leave `domain` out unless the user asked for a specific address.
3. Share the returned URL. If the result says the site is in preview mode, tell the user that it expires in one hour and which limit caused it.
4. If a publish result is unclear, call `list_sites` before trying again, so the user does not end up with duplicate sites.
5. To change an existing site, confirm the domain and that its current content will be replaced, then call `update_site`.
6. To delete, confirm the exact domain with the user first, one site at a time, then call `delete_site`.
7. Tiiny Host only reaches sites of the connected account. If a tool says a site was not found or is not owned by the user, say so and do not retry with other domains.
