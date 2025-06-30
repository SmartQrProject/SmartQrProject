# 🔁 CI/CD con GitHub Actions

## 🔐 SSH y secrets

- Se generó una clave SSH para acceso desde GitHub Actions al servidor Oracle
- `KNOWN_HOSTS` y `SSH_PRIVATE_KEY` cargados como secrets

## ⚙️ Workflow

```yaml
name: Deploy SmartQR Backend

on:
  push:
    branches: [dev]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup SSH
        uses: webfactory/ssh-agent@v0.7.0
        with:
          ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}

      - name: Deploy via SSH
        run: |
          ssh -o StrictHostKeyChecking=no ubuntu@<ip> << 'EOF'
            cd ~/SmartQr-Back/smart-qr-app
            git pull origin dev
            docker compose down
            docker compose up -d --build
            docker ps | grep smartqr-backend || exit 1
          EOF
```
