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


