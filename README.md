### Semantic Versioning

An action to make semantic versions in a repository.

Example:
```yaml
name: Create versions
on:
  workflow_dispatch:
  push:
    paths-ignore:
      - "docs/**"
      - "README.md"

jobs:
  build:
    runs-on: "ubuntu-latest"
    steps:

      - name: Create versions
        id: versions
        uses: voplica/sem-ver-action@v1
        with:
          gitHubToken: "${{ secrets.GITHUB_TOKEN }}"

      - name: Print versions
        run: |
          echo "Version: ${{ steps.versions.outputs.ver_semVerNoMeta }}"
          echo "Tag: ${{ steps.versions.outputs.ver_tag }}"
          echo "Labels: ${{ steps.versions.outputs.oci_labels }}"
          echo "Docker simple tags: ${{ steps.versions.outputs.docker_simple_tags }}"
```
