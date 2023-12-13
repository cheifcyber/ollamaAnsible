# ollamaAnsible

This repository contains the necessary files to deploy the Ollama Docker container to a TensorDock Ubuntu 22.04 environment using Ansible.

## Files

### motd

This is an empty motd file, my ansible playbook copies an motd file because I like cool ascii art for my servers motd. You should make or find some to put in it. You can also do ascii block text by installing figlet

```
apt install -y figlet
echo "ollama" | figlet
```

### docker-compose.yml

This file contains the Docker Compose configuration for the Ollama service.

### ollama.yml

This file contains the Ansible playbook for setting up the server. It includes a task that copies a Message of the Day (motd) file to the server. This file is currently blank, but you can add your own ASCII art or other message.

### inventoryExample.yml

This file is an example inventory file for Ansible. You will need to replace the values in the double brackets {{}} with the actual values for your server.

```
ollama:
  hosts:
    {{your_ip}}:
      ansible_port: {{port}}
      ansible_user: {{user}}
      ansible_ssh_private_key_file: {{/path/to/key}}
```

Replace {{your_ip}} with the IP address of your server, {{port}} with the SSH port, {{user}} with the SSH username, and {{/path/to/key}} with the path to your SSH private key file.

You can use the following command to replace the placeholders with your actual values. Replace `your_actual_ip`, `your_actual_port`, `your_actual_user`, and `/your/actual/path/to/key` with your actual values. This command will edit `inventoryExample.yml` and output the edited inventory file to inventory.yml

```
sed 's/{{your_ip}}/your_actual_ip/g; s/{{port}}/your_actual_port/g; s/{{user}}/your_actual_user/g; s|{{/path/to/key}}|/your/actual/path/to/key|g' inventoryExample.yml > inventory.yml
```


### ollamaAPIDocs.md

The [ollamaAPIDocs.md](./ollamaApiDocs.md) file is the documentation for the ollama API and is copied here for ease of access

## Requirements

You will need to have Ansible and the Ansible playbook plugin installed on your machine. You can then run the playbook with the following command:

```
ansible-playbook -i inventory.yml ollama.yml
```