# Helm chart: web-app

This chart deploys `web-app` independently.

## Expected image

```text
<AWS_ACCOUNT_ID>.dkr.ecr.<REGION>.amazonaws.com/web-app:<GIT_SHA>
```

## Local validation

```bash
helm lint ./helm
helm template web-app ./helm \
  --set image.repository=example/web-app \
  --set image.tag=dev
```

## Notes

- RollingUpdate: `maxUnavailable=0`, `maxSurge=1`.
- Readiness/liveness probes are enabled by default.
- HPA is disabled by default.
- Adjust `values.yaml` if the application uses another port or health endpoint.
