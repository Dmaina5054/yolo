## `Ansible Project: Server Provisioning`

`This project provides Ansible playbooks for provisioning various server types in your infrastructure, automating the setup process for a robust and consistent environment.`

### `Project Structure`

`The project utilizes a modular structure with the following directories:`

- `**ansible.cfg**: Global Ansible configuration file.`
- `**hosts**: Inventory file defining managed servers.`
- `**playbook.yaml**: Main playbook orchestrating the overall provisioning process.`
- `**roles**: Directory containing reusable roles for server provisioning. Each role has its own subdirectories:`
    - `**defaults**: Default variables specific to the role.`
    - `**files**: Static files to be deployed to the server.`
    - `**handlers**: Additional tasks to be executed based on certain conditions.`
    - `**meta**: Role metadata file.`
    - `**README.md**: Optional readme for the specific role.`
    - `**tasks**: Main tasks for provisioning the server.`
    - `**templates**: Jinja2 templates used within the role tasks.`
    - `**tests**: Optional directory for unit tests of the role (inventory and test.yml files).`
    - `**vars**: Additional variables specific to the role.`

### `Roles`

`This project currently includes roles for provisioning the following server types:`

- `**admin_server_provisioner**: Sets up an administration server.`
- `**backend_server_provisioner**: Sets up backend servers.`
- `**frontend_server_provisioner**: Sets up frontend servers.`
- `**mongodb_server_provisioner**: Sets up MongoDB servers.`

### `Usage`

`**Prerequisites:**`

- `Ansible installed and configured (refer to official Ansible documentation for installation steps).`
- `Python interpreter (version supported by your Ansible version).


deployed frontend-url : http://34.35.31.72:3000