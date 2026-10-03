# CEP-Admin

Fybud platform admin (org management). Deployed separately from client CEP.

```
CEP-Admin/
  backend/                  ← admin API (fybud/cep-admin-api)
  frontend/                 ← admin SPA (fybud/cep-admin)
  docker-compose.deploy.yml ← Fybud Deploy runtime contract
  .github/workflows/…       ← build → Hub → Deploy webhook
```

- Web: `cep-admin.fybud.com`
- API: `api.cep-admin.fybud.com`
- Playbook: [`DEPLOY.md`](./DEPLOY.md) · rules: [`AGENTS.md`](./AGENTS.md)
- Client product: [Fybud/CEP](https://github.com/Fybud/CEP) (`platform-api` is cloned into the admin-api image for tenant Prisma)

Push to `main` → Actions builds images → Fybud Deploy pulls + publishes. Paste secrets once in the Deploy UI, then approve.

### Local backend without Docker

Symlink CEP’s `platform-api` next to `backend/` so tenant imports resolve:

```bash
# from CEP-Admin root
ln -s ../CEP/platform-api platform-api   # or `mklink /J platform-api ..\CEP\platform-api` on Windows
```
