## How to install packages on macOS

1. Install Ansible if you haven't already:
   ```sh
   brew install ansible
   ```

2. Run the following command to install packages on your Mac:
   ```sh
   ansible-playbook -i inventories/local/hosts playbooks/mac.yml
   ```

This will automatically install Homebrew (if not present) and then install all packages defined for macOS.