# Learn OpenShift Book: Study Lab

Hands-on notes, commands and YAML files from working through **Learn OpenShift, Second Edition** (Packt), as preparation for the **Red Hat Certified System Administrator in OpenShift (EX280)** exam.

Each chapter folder holds what I built while studying that chapter, plus my solutions to the matching EX280 practice questions, so everything can be reapplied to a fresh cluster.

## Lab environment

| Item | Details |
| --- | --- |
| Cluster | Red Hat OpenShift Service on AWS (ROSA) with hosted control planes (HCP) |
| OpenShift version | 4.22 |
| Worker nodes | Two m5.xlarge nodes in a single availability zone |
| Region | AWS ca-central-1 (Canada Central) |
| Workstation | AlmaLinux on WSL (Windows Subsystem for Linux), with the `rosa`, `oc` and `aws` command-line tools |
| Developer chapters | Red Hat Developer Sandbox |

With HCP, Red Hat runs the control plane in its own AWS account, and only the worker nodes run in mine. That keeps the cluster cheap and quick to build, which suits a lab that is created for each study session and deleted afterwards.

## Study workflow

1. **Rebuild** the cluster before each study session (about 20 to 30 minutes).
2. **Study** the chapter, saving every YAML file and command into its folder here.
3. **Practise** the EX280 questions that match the chapter.
4. **Commit and push** the work to this repository.
5. **Delete** the cluster afterwards so it only costs money while I am studying.

Because the cluster is deleted after each session, this repository is the record of everything built on it. Anything saved here can be reapplied to the next cluster with `oc apply -f <file>`.

## Repository structure

```
Learn-OpenShift-Book/
├── README.md
├── setup/                  # cluster rebuild and teardown commands
├── chapter-05-auth/        # authentication and authorization
├── chapter-06-scalability/
├── chapter-07-security/
├── chapter-08-storage/
├── chapter-09-developing/
├── chapter-10-deployment/
├── chapter-11-helm-kustomize/
├── ...
└── ex280-practice/         # solutions to the EX280 practice questions
```

## Chapter progress

| Chapter | Topic | Lab | Status |
| --- | --- | --- | --- |
| 1 | Understanding Containers | WSL | Reviewed |
| 2 | Kubernetes and OpenShift | Sandbox | Reviewed |
| 3 | Getting Started with OpenShift | ROSA | Reviewed |
| 4 | Post-Install Configuration | Read only | Reviewed |
| 5 | Authentication and Authorization | ROSA | In progress |
| 6 | Scalability | ROSA | Not started |
| 7 | Application Security and Isolation | ROSA | Not started |
| 8 | Persistent Storage | ROSA | Not started |
| 9 | Developing for OpenShift | Sandbox | Not started |
| 10 | Deployment to OpenShift | Sandbox | Not started |
| 11 | Helm and Kustomize | Sandbox | Not started |
| 12 | Logging | ROSA | Not started |
| 13 | Monitoring | ROSA | Not started |
| 14 | Service Mesh and Distributed Tracing | ROSA | Not started |
| 15 | Additional Services | ROSA | Not started |
| 16 | Operators and the Operator Framework | ROSA | Not started |
| 17 | Upgrading OpenShift | ROSA | Not started |
| 18 | Troubleshooting and Maintenance | ROSA | Not started |

## ROSA differences from the book

The book builds a self-managed cluster on VMware vSphere. On ROSA, a few tasks are done differently:

- **Identity providers** are added with `rosa create idp` instead of editing the OAuth resource.
- **There is no kubeadmin user**; admin access comes from `rosa create admin`.
- **Infrastructure nodes, node SSH and some cluster-wide settings** are managed by Red Hat, so those sections are read only.

## Security note

This is a public repository. Passwords, tokens, kubeconfig files, private keys and AWS account details are never committed; see `.gitignore`.

## References

- Book: *Learn OpenShift, Second Edition* (Packt)
- Book code: https://github.com/PacktPublishing/Learn-OpenShift-Second-Edition
- ROSA documentation: https://docs.openshift.com/rosa/
