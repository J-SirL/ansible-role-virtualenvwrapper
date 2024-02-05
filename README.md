# Ansible Role for Virtualenvwrapper

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Role Structure](#role-structure)
- [Role Variables](#role-variables)
- [Example Playbook](#example-playbook)
- [License](#license)
- [Author](#author)

## Overview
This Ansible role, created by Johan Sörell, automates the setup and management of Virtualenvwrapper. It is designed to enhance the usability of Python's virtualenv by providing structured commands for creating, removing, listing, and switching between Python virtual environments.

## Key Features
- **Automated Installation**: Streamlines the installation of Virtualenvwrapper.
- **Environment Management**: Simplifies the process of managing Python virtual environments.
- **Flexible and Customizable**: Allows customization for different users and environments through variables and templates.

## Role Structure
- `defaults/main.yml`: Defines default variables for user and virtual environment settings.
- `tasks`: Contains Ansible tasks for various operations like creating and removing virtual environments.
- `templates/virtualenvwrapper.sh.j2`: Jinja2 template for initializing Virtualenvwrapper.

## Role Variables
The role uses several variables defined in `defaults/main.yml` for customization:

- `virtualenvwrapper_user`: Specifies the user for whom Virtualenvwrapper will be set up. Default is `jsorell`.
- `virtualenv_settings`: A list of dictionaries defining settings for different virtual environments. Each entry can specify:
  - `project_home`: The home directory for the project.
  - `env_name`: The name of the virtual environment.
  - `description`: A description of the project or environment.
  - `github_url`: The URL of the project's GitHub repository.
  - `workon_home`: The directory where virtual environments are stored.
  - `virtualenvwrapper_python`: Path to the Python interpreter.
  - `virtualenvwrapper_script`: Path to the Virtualenvwrapper initialization script.
- `default_project_home`, `default_workon_home`, `default_python_path`, `default_virtualenvwrapper_path`: Default paths and settings for the virtual environments.
- `virtualenv_tasks`: Defines tasks for creating, removing, listing, and managing virtual environments. Each task can be customized with conditions.

## Example Playbook
Here's an example playbook demonstrating how to use this role:

```yaml
- hosts: all
  roles:
    - { role: ansible-role-virtualenvwrapper, virtualenvwrapper_user: 'your_username' }
  vars:
    virtualenv_settings:
      - env_name: 'my_env'
        project_home: '/path/to/project'
        # Other settings as needed
```

Replace `your_username` and other placeholders with the appropriate values as per your requirements.

## License
This project is licensed under the GNU General Public License v3.0 (GPL-3.0), as found in the LICENSE file.

## Author
Johan Sörell - [GitHub](https://github.com/J-SirL/ansible-role-virtualenvwrapper)