# 🐳 Guide to Using Node Images on GHCR

Available images:

- `ghcr.io/unich-labs/node:20-slim`
- `ghcr.io/unich-labs/node:22-slim`
- `ghcr.io/unich-labs/node:24-slim`
- `ghcr.io/unich-labs/node:lts-slim`

## ✅ 1. Create a GitHub Personal Access Token (PAT)

1. Go to: [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **"Generate new token (classic)"**
3. Grant the following permission:
    - ✅ `read:packages`
4. Click "Generate token" and **copy it immediately** (you won't be able to view it again)

## 🔐 2. Login to GitHub Container Registry (GHCR) via Docker

```bash
echo YOUR_TOKEN | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
```

- Replace YOUR_TOKEN with the token you generated
- Replace YOUR_GITHUB_USERNAME with your GitHub username

## 📦 3. Use the Image in Your Dockerfile

You can use any of the available images as a base in your own Dockerfile:

```bash
FROM ghcr.io/unich-labs/node:20-slim AS base
```

Or pull directly:

```bash
docker pull ghcr.io/unich-labs/node:20-slim
```

## ⚠️ Notes

- While the images are public, logging in with a token helps you avoid GitHub’s anonymous rate limits.
- The token only needs the read:packages scope and does not require access to any repositories.
- Safe to use in CI/CD pipelines, local development, or container registries.

## 📄 License

These base images are based on the official Node.js Docker images and are redistributed under the same license (MIT and
Node.js licenses).

