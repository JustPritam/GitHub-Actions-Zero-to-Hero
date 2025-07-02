# GitHub-Actions-Zero-to-Hero 
Repository to kick start your journey with GitHub Actions

## Comparing with Jenkins 

### Advantages of GitHub Actions over Jenkins

- Hosting: Jenkins is self-hosted, meaning it requires its own server to run, while GitHub Actions is hosted by GitHub and runs directly in your GitHub repository.

- User interface: Jenkins has a complex and sophisticated user interface, while GitHub Actions has a more streamlined and user-friendly interface that is better suited for simple to moderate automation tasks.

- Cost: Jenkins can be expensive to run and maintain, especially for organizations with large and complex automation needs. GitHub Actions, on the other hand, is free for open-source projects and has a tiered pricing model for private repositories, making it more accessible to smaller organizations and individual developers.

### Advantages of Jenkins over GitHub Actions

- Integration: Jenkins can integrate with a wide range of tools and services, but GitHub Actions is tightly integrated with the GitHub platform, making it easier to automate tasks related to your GitHub workflow.

In conclusion, Jenkins is better suited for complex and large-scale automation tasks, while GitHub Actions is a more cost-effective and user-friendly solution for simple to moderate automation needs.

## Github hosted agents VS Self hosted agents

| Feature / Aspect          | **GitHub-hosted Agent**                                  | **Self-hosted Agent**                                    |
| ------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| **Ownership**             | Managed by GitHub                                        | Managed by you (your VM, container, or machine)          |
| **Setup & Maintenance**   | No setup required — GitHub provides everything           | You install and maintain the agent manually              |
| **Hardware/Infra Cost**   | Free (with limits) or billed as per GitHub plan          | You bear the infrastructure cost                         |
| **Customization**         | Limited (fixed VM image, can't pre-install custom tools) | Full control over software, environment, hardware        |
| **Execution Time Limits** | Strict (e.g., 2,000 free minutes/month on Free tier)     | You control it — no enforced time limits by GitHub       |
| **Performance**           | Shared runners — might queue during peak times           | Dedicated runner — consistent performance                |
| **Scaling**               | Automatically scaled by GitHub                           | You handle scaling and concurrency                       |
| **Security**              | GitHub sandboxed runners — lower control, higher trust   | Higher control, but you must ensure security hardening   |
| **Network Access**        | Limited — public internet only                           | Can access internal servers, databases, private networks |
| **Caching/Artifacts**     | Ephemeral runners — limited cache reuse                  | Persistent — better cache, reuse dependencies            |

### When to use what?

| Scenario                                 | Recommendation        |
| ---------------------------------------- | --------------------- |
| Quick setup, standard builds/tests       | ✅ GitHub-hosted Agent |
| Custom environment, private infra access | ✅ Self-hosted Agent   |
| Need cost control and high concurrency   | ✅ Self-hosted Agent   |
| Experimental/open-source projects        | ✅ GitHub-hosted Agent |

### How to use EC2 instance as self hosted runner?

After setting up the EC2 instance follow these steps:
- Go to your repo → Settings → Actions → Runners → New self-hosted runner
- Choose Linux x64, and GitHub will give you instructions.

## How to create this pipeline?

- GitHub automatically detects YAML files in .github/workflows/ (This location has to be created manually).

- Based on the triggers (on:), it runs the defined jobs.

- Each job runs in a GitHub-hosted runner (like Ubuntu, Windows, etc.).

## How to add secrets?

If you want to use secrets in GitHub Actions, like API keys, passwords, or tokens, here's exactly how to do it step by step:

🔐 **Step 1**: Add Secrets in GitHub
- Go to your GitHub repository.
- Click on Settings → Secrets and variables → Actions.
- Click New repository secret.
- Enter:
  Name: MY_SECRET_TOKEN
  Value: super-secret-value
- Now the secret is securely stored — GitHub encrypts it.

⚙️ **Step 2**: Use the Secret in Workflow
- In your .github/workflows/ci.yml file, reference it like this:
```
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Print secret (for demo only - don’t do this in real workflows)
        run: echo "${{ secrets.MY_SECRET_TOKEN }}"
```
**🔥** Never print secrets in real workflows — this is just to show how it's accessed.

### NOTE: A sample yml file is stored in this repo in the .github/workflows/ where there is explanation of the YML file.


