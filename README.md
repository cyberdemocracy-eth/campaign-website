# CyberDemocracy.ETH - Iran's Digital Civic Defense

A Jekyll-based static website deployed on IPFS for censorship-resistant hosting.

## 🚀 Quick Start

### Local Development

1. **Install Ruby and Jekyll:**
   ```bash
   # On macOS with Homebrew
   brew install ruby
   gem install bundler jekyll
   ```

2. **Install dependencies:**
   ```bash
   bundle install
   ```

3. **Run locally:**
   ```bash
   bundle exec jekyll serve
   ```
   
   Visit `http://localhost:4000`

### Build for Production

```bash
bundle exec jekyll build
```

The static site will be generated in the `_site` folder.

## 🌐 IPFS Deployment

This site uses [ipfs-deploy-action](https://github.com/ipshipyard/ipfs-deploy-action) for automatic IPFS deployment.

**Repository:** [github.com/Iranians-Vote-Digital-Democracy](https://github.com/Iranians-Vote-Digital-Democracy)

### Setup Storacha (Required)

1. Install w3cli:
   ```bash
   npm install -g @web3-storage/w3cli
   ```

2. Login to Storacha:
   ```bash
   w3 login
   ```

3. Create a new space:
   ```bash
   w3 space create cyberdemocracy
   ```

4. Create a signing key:
   ```bash
   w3 key create --json
   ```
   Save the `key` value as `STORACHA_KEY` secret in GitHub.

5. Create a proof:
   ```bash
   w3 delegation create <DID_FROM_KEY> -c space/blob/add -c space/index/add -c filecoin/offer -c upload/add --base64
   ```
   Save the output as `STORACHA_PROOF` secret in GitHub.

### GitHub Secrets Required

Add these secrets to your GitHub repository (Settings → Secrets and variables → Actions):

| Secret | Description |
|--------|-------------|
| `STORACHA_KEY` | Base64 encoded key from `w3 key create --json` |
| `STORACHA_PROOF` | Base64 encoded UCAN proof from `w3 delegation create` |
| `PINATA_JWT_TOKEN` | (Optional) Pinata JWT for redundant pinning |

### Automatic Deployment

Every push to `main` will:
1. Build the Jekyll site
2. Deploy to IPFS via Storacha
3. Pin the content
4. Add preview links to PR comments and commit status

## 📁 Project Structure

```
cyberdemocracy.eth/
├── _config.yml          # Jekyll configuration
├── _layouts/
│   └── default.html     # Main layout with styling
├── index.html           # Homepage content
├── Gemfile              # Ruby dependencies
├── .github/
│   └── workflows/
│       └── deploy-ipfs.yml  # GitHub Actions workflow
└── README.md
```

## 🔗 Access Methods

After deployment, access the site via:

- **IPFS Gateway:** `https://<CID>.ipfs.dweb.link`
- **IPFS Native:** `ipfs://<CID>`
- **ENS + IPFS:** Configure your ENS domain to point to the IPFS CID

### Linking to ENS Domain

To link your `cyberdemocracy.eth` ENS domain:

1. Get the CID from the deployment
2. Go to [app.ens.domains](https://app.ens.domains)
3. Edit your domain's records
4. Set the Content Hash to: `ipfs://<CID>`

## 🛡️ Why IPFS?

- **Censorship Resistant:** No single point of failure
- **Immutable:** Content cannot be altered once published
- **Distributed:** Hosted across multiple nodes worldwide
- **Verifiable:** Content addressed by cryptographic hash

## 📊 Data Sources

Casualty figures sourced from:
- [Wikipedia: 2025–2026 Iranian protests](https://en.wikipedia.org/wiki/2025%E2%80%932026_Iranian_protests)
- Iran International (13 January 2026)
- HRANA (Human Rights Activists in Iran)

## 📜 License

This content is published for humanitarian purposes under the Responsibility to Protect (R2P) doctrine.

---

**Forward this globally—9M in 72 hours changes everything.**

Wallet: `Cyberdemocracy.ETH`
