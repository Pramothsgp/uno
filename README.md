# App template

Next.js app, built into a container and deployed to Cloud Run.

- `npm run dev` for local work. `docker build -t app . && docker run -p 8080:8080 app` to test the image.
- Push to `main`: CI lints, builds the image, pushes it to Artifact Registry and bumps `apps/<repo>/dev.yaml` in the `deployments` repo. Dev deploys from there.
- Prod: run the `promote` workflow in `deployments` and approve the `prod` environment.

Repos made from this template get their variables (`IMAGE`, `CI_SA`, `WIF_PROVIDER`, `GCP_REGION`) and the `DEPLOYMENTS_DEPLOY_KEY` secret from Terraform in the `platform` repo. Don't set them by hand.
