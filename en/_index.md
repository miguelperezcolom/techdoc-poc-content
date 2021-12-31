---
title : "POC Tech Doc"
linkTitle : "POC Tech Doc"

---


## Requisites for tech doc platform

- enable "doc as code"
- keep doc in git repo (enable pull requests, blame, ...)
- use md, asciidoc, ...
- distributable through CDN (e.g. Netlify)
- easy CI/CD (Repo --> Netlify --> Published)
- do not use own resources (no need to configure/maintain anything)
- integrate doc from code (e.g. openapi, c#, ...)
- printer friendly
- searchable
- include content folder as a git submodule / from several sources (push should trigger site build)

## Pending

- protect with corporate OAuth

