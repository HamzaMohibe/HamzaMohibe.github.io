+++
archetype = "chapter"
title = "Production Deployment"
weight = 11
+++

# Deployment Tool Considerations

When choosing a deployment tool, it's essential to consider various factors based on your use case and technology stack. Here are some considerations for comparing Git Actions and Jetty:

### Use Case and Technology Stack
- **Jetty**: Suited for deploying Java-based web applications.
- **Git Actions**: Versatile CI/CD tool for various application types.

### Complexity
- Jetty might involve more setup compared to Git Actions, which is a managed CI/CD service.

### Integration
- Git Actions seamlessly integrates with GitHub repositories for triggering deployments based on repository events.
- Jetty requires server-level configuration and management.

### Scalability
- Jetty is capable of handling high loads and supports scalable deployments.
- Git Actions provides scalable CI/CD workflows but isn't a server or application container itself.

Ultimately, the choice between Git Actions and Jetty depends on your application's technology stack, deployment requirements, scalability needs, and familiarity with the tools. In some scenarios, a combination of both tools might be beneficial.

# Security and Optimization in GitHub Actions for Azure VM Deployment

In an effort to improve security practices, error handling, and optimize deployment, several adjustments have been made to the GitHub Actions workflow for deploying to an Azure VM:

## Security Practices

### 1. Secure Handling of SSH Key
- SSH key stored in a GitHub secret (`AZURE_VM_SSH_KEY`) and retrieved within the workflow using `${{ secrets.AZURE_VM_SSH_KEY }}`.
- SSH key written to a file (`~/.ssh/id_rsa`) within the runner environment to avoid direct exposure.

### 2. Restricting SSH Key Permissions
- Permissions for the SSH key file (`~/.ssh/id_rsa`) set to read-only for the owner (`chmod 600 ~/.ssh/id_rsa`) to limit access.

### 3. Known Hosts Verification
- `ssh-keyscan` used to fetch Azure VM's public key and add it to the `known_hosts` file to prevent potential MitM attacks.

## Error Handling

### 1. Explicit Branch Reset
- Script fetches latest changes and resets to the remote branch (`git fetch`, `git reset --hard origin/$GITHUB_BRANCH`) for a clean deployment state.

### 2. Validation of Git Repository
- Checks the presence of a Git repository (`$GITHUB_REPO_PATH/.git`) to prevent errors during cloning or pulling.

## Optimizations

### 1. Simplified SSH Key Handling
- SSH key read directly from the GitHub secret without additional encoding steps.

### 2. Reduced Redundant Commands
- Optimized git commands to fetch and reset branches, reducing redundancy and potentially speeding up deployments.

### 3. Known Hosts Update
- Ensures Azure VM's public key is updated in the `known_hosts` file for secure SSH connections.

These adjustments aim to enhance security, error handling, and optimize the deployment process for Azure VM deployments. Always test thoroughly and adapt as per specific use cases and security requirements.
