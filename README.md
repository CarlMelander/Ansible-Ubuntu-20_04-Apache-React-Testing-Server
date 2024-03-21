# React App Deployment Playbook

This Ansible playbook is designed for setting up a Linux server to serve a React website using Apache. It automates the process from the system update to the deployment of a React project cloned from a GitHub repository.

## Core Functions

- Updates the apt package cache.
- Installs Apache and Git.
- Clones the React project from the specified GitHub repository to `/var/www/react-app`.
- Installs Node.js to support React app dependencies.
- Configures Apache to serve the React app using a provided template.
- Generates an OpenSSL private key and a self-signed SSL certificate for secure communication.
- Configures Apache to use the self-signed SSL certificate.
- Enables the Apache SSL site and module, and disables the default site.

## Dependencies

Ensure you have Ansible installed on your system. This playbook is intended for development environments as it uses a self-signed SSL certificate. You might need to adjust the playbook variables and paths according to your project's structure and requirements.

### GitHub Project Configuration

The playbook expects the React project to be hosted on GitHub. Specify the repository by replacing `github/rep/` in the playbook with your repository's URL. Ensure your server has access to clone the repository.

### SSL Configuration

This playbook uses a self-signed SSL certificate for development purposes. It's recommended to replace it with a valid certificate for production environments.

## Usage

1. Update the `domain_name` variable in the playbook with your domain.
2. Place your Apache configuration template in the specified `src` path.
3. Run the playbook using the following command:

```sh
ansible-playbook playbook.yml -i inventory
