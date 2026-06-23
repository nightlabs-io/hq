# nightlabs.io

Source for **[nightlabs.io](https://nightlabs.io)** — the personal site and engineering portfolio of **John Cuckovich, Principal Platform Engineer** (17 years in production; NOC technician to principal on a single service-provider platform).

The site exists to replace "request access" with a full view. Two of the featured projects live in private repositories; rather than gate everything behind an access request, each one is presented as a detailed public case study — architecture, decisions, and results — with code access available on request.

## Site map

| Page | URL | What it is |
| --- | --- | --- |
| Landing | `/` | Dark terminal-styled profile: who, what, the career path, the stack, and selected work. |
| Kubernetes Diagnostic Agent | `/k8s-diag-agent/` | Case study — a read-only LLM tool-calling agent that diagnoses live k3s clusters against a failure-injection harness. Private repo. |
| Golden-Image Build Pipeline | `/golden-image-build-pipeline/` | Case study — a Packer/QEMU/Docker delivery pipeline with a QEMU boot-validation gate. Private repo. |
| vault-fargate-aurora | `/vault-fargate-aurora/` | Case study — HashiCorp Vault deployed HA on AWS ECS Fargate with Aurora storage, KMS auto-unseal, and a warm DR region. [Public repo](https://github.com/jpcuckovi/vault-fargate-aurora). |

The landing page links into each case study; each case study links back to the landing.

## Structure

```
.
├── CNAME                              # custom domain: nightlabs.io
├── index.html                         # landing page
├── k8s-diag-agent/index.html          # case study
├── golden-image-build-pipeline/index.html
└── vault-fargate-aurora/index.html
```

Each `index.html` is a self-contained page that renders client-side (React + IBM Plex fonts loaded from CDN). There is no build step — the files are served as-is.

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

A local server is required (rather than opening the files directly) so the absolute case-study links resolve.

## Deployment

Served via GitHub Pages from the default branch. The `CNAME` file points the site at `nightlabs.io`; DNS for that domain must target GitHub Pages.
