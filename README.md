# CEP-Admin

Fybud platform admin (org management). Deployed separately from client CEP.

- Images: `fybud/cep-admin-api`, `fybud/cep-admin`
- Deploy compose: root [`docker-compose.deploy.yml`](./docker-compose.deploy.yml)
  - Web: `cep-admin.fybud.com`
  - API: `api.cep-admin.fybud.com`
- Playbook: [`DEPLOY.md`](./DEPLOY.md) · rules: [`AGENTS.md`](./AGENTS.md)
- Client product: [Fybud/CEP](https://github.com/Fybud/CEP)

Push to `main` → Actions builds images → Fybud Deploy pulls + publishes. Paste secrets once in the Deploy UI, then approve.
