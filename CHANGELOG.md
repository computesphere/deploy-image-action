# **Changelog**
Changes to the ComputeSphere Deploy Image Action will be documented in this file.

## **Versioning**
ComputeSphere Deploy Image Action follows [Semantic Versioning](https://semver.org/) (`MAJOR.MINOR.PATCH`):  
- **MAJOR**: Breaking changes (incompatible API/usage changes).  
- **MINOR**: New features that are backward compatible.  
- **PATCH**: Bug fixes, documentation updates, and minor improvements.  

---

## **[v1.0.0] - 2025-03-18**
### Initial Release
- Supports deploying private and public container images to ComputeSphere.
- Accepts authentication credentials for private images.
- Allows specifying container registry provider (`ecr`, `gcr`, `other`).
- Supports multiple registries.

---

## **How to Upgrade**
To upgrade to the latest version, update your workflow file:

```yaml
uses: computesphere/deploy-image-action@v1
```
