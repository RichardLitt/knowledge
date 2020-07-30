# Dockerfiles

Docker images don't have the same sort of metadata needs as npm packages or GitHub packages, as far as I can tell. However, there are basic documentation needs that should be met:
- Include a license
- Include a README
- Include a [`LABEL`](https://docs.docker.com/engine/reference/builder/#label) field in your Dockerfile for each of the following:
  - `Maintainer`
  - `Description`
  - `Tags` (probably a string field - debatable if this is useful)

# Crates.io

This is much more similar to npm. Fill out [this data](https://doc.rust-lang.org/cargo/reference/manifest.html#package-metadata) in the `Cargo.toml` file.