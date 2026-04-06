# Chartline AI

AI consulting business. Client projects are managed as separate repos under the [Chartline-AI](https://github.com/Chartline-AI) GitHub organization.

## Repo Structure

Each client gets their own private repo:

```
Chartline-AI/clientname-website   # static site (GitHub Pages)
Chartline-AI/clientname-app       # web app (Vercel, Railway, etc.)
```

Internal tools and templates also live here:

```
Chartline-AI/chartline-ai         # company website (this repo)
Chartline-AI/lead-gen             # lead generation pipeline
```

## Adding a Client to Their Repo

Clients are added as **outside collaborators** with write access to their specific repo only. This is free and gives them no visibility into other repos.

```bash
gh api repos/Chartline-AI/clientname/collaborators/THEIR_USERNAME -X PUT -f permission=push
```

Replace `clientname` with the repo name and `THEIR_USERNAME` with the client's GitHub username.

The client will receive an email invitation they must accept before access is granted.

### Permission Levels

| Permission | Use Case |
|---|---|
| `push` (write) | Client can push changes, create branches, open PRs |
| `pull` (read) | Client can only view and clone the repo |
| `admin` | Full control including settings — rarely needed |

## New Client Onboarding

1. **Create the repo:**
   ```bash
   gh repo create Chartline-AI/clientname-website --private --description "Client Name - website"
   ```

2. **Initialize with project template** (Jekyll for Pages, Next.js for apps, etc.)

3. **Enable GitHub Pages** (if static site):
   - Repo Settings → Pages → Source: Deploy from branch (`main`)

4. **Add the client as a collaborator:**
   ```bash
   gh api repos/Chartline-AI/clientname-website/collaborators/THEIR_USERNAME -X PUT -f permission=push
   ```

5. **Clone locally:**
   ```bash
   cd ~/Chartline/Projects
   git clone https://github.com/Chartline-AI/clientname-website.git
   ```

## Removing a Client

```bash
gh api repos/Chartline-AI/clientname/collaborators/THEIR_USERNAME -X DELETE
```

## Local Development

All projects live locally at `~/Chartline/Projects/`. Each subdirectory has its own git repo pointing to its org repo.
