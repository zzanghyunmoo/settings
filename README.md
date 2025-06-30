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

## How to install packges on Linux (Debian)

1. Install Ansible if you haven't already:
   ```sh
   sudo apt-get install ansible-core
   ```

2. Run the following command to install packages on your Linux:
   ```sh
   ansible-playbook -i inventories/local/hosts playbooks/linux.yml --ask-become-pass
   ```

3. 만약 ansible 버전이 낮다면, 다음 명령어를 이용해 업그레이드가 가능합니다.
   ```sh
   sudo apt update
   sudo apt install python3 python3-pip -y
   pip3 install --upgrade ansible
   ```