# **ComputeSphere Deploy Image GitHub Action**

This GitHub Action allows you to **deploy a container image** to your [ComputeSphere](https://computesphere.com) environment by adding a step to your workflow.

---

## **Usage Examples**

### **Deploy a Private Image**

This example **deploys a private image** from a container registry that requires authentication.

```yaml
- name: Deploy Private Image to ComputeSphere
  uses: computesphere/deploy-image-action@v1
  with:
    name: ${{ vars.IMAGE }}
    account_id: ${{ secrets.COMPUTESPHERE_ACCOUNT_ID }}
    token: ${{ secrets.COMPUTESPHERE_API_TOKEN }}
    deployment_id: ${{ vars.DEPLOYMENT_ID }}
    registry: ${{ vars.REGISTRY }}
    type: private
    username: ${{ secrets.REGISTRY_USERNAME }}
    password: ${{ secrets.REGISTRY_PASSWORD }}
```

**`username` & `password`** are provided for authentication to private registries.
**Provider defaults to `other`** if undefined.

---

### **Deploy a Public Image**

If you are deploying a **public container image** (no authentication required), omit `username` and `password`:

```yaml
- name: Deploy Public Image to ComputeSphere
  uses: computesphere/deploy-image-action@v1
  with:
    name: ${{ vars.IMAGE }}
    account_id: ${{ secrets.COMPUTESPHERE_ACCOUNT_ID }}
    token: ${{ secrets.COMPUTESPHERE_API_TOKEN }}
    deployment_id: ${{ vars.DEPLOYMENT_ID }}
    registry: ${{ vars.REGISTRY }}
```

**No authentication needed** for public images.
**Provider defaults to `other`** if undefined.
**Type defaults to `public`** if undefined.

---

## **Inputs**

| Input           | Description                                                                                  | Required | Default      |
| --------------- | -------------------------------------------------------------------------------------------- | -------- | ------------ |
| `name`          | Full image name with tag (e.g., `quay.io/computesphere/computesphere-nodejs-example:v0.0.1`) | ✅ Yes   | -            |
| `account_id`    | ComputeSphere account ID (`X-Account-ID` header)                                             | ✅ Yes   | -            |
| `token`         | ComputeSphere API token (`X-User-Token` header)                                              | ✅ Yes   | -            |
| `deployment_id` | ComputeSphere Deployment ID                                                                  | ✅ Yes   | -            |
| `registry`      | Container registry URL (e.g., `quay.io`)                                                     | ✅ Yes   | -            |
| `provider`      | Image provider (`other`, `ecr`, `gcr`)                                                       | ❌ No    | `other`      |
| `type`          | Image type (`private` or `public`)                                                           | ❌ No    | `public`     |
| `username`      | Container registry username (for private images)                                             | ❌ No    | `''` (empty) |
| `password`      | Container registry password (for private images)                                             | ❌ No    | `''` (empty) |

## 💡 **If `type` is `public`, `username` and `password` are ignored.**

## **Learn more**

- **ComputeSphere Docs**: [https://computesphere.com/docs](https://computesphere.com/docs)
- **GitHub Actions Guide**: [https://docs.github.com/en/actions](https://docs.github.com/en/actions)
