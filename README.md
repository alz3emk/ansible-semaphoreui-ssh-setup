### ANSIBLE SEMAPHORE UI - SSH-KEY SETUP 

## ANSIBLE SEMAPHORE Machine / Docker Container of SEMAPHORE UI

To establish SSH connectivity for managing remote servers through Ansible SEMAPHORE GUI, follow these steps:

### Generating SSH Keys

On the controlling server or Docker container of SEMAPHORE UI:

1. Run the command `sudo ssh-keygen -t rsa` to generate SSH keys.
2. Name the keys arbitrarily, e.g., YourKeyNameCanBeAnything.
3. This process will generate both public and private keys.
4. Retrieve the public key by executing `cat YourKeyName` and then copy it.

### Setting Up Remote Server

Perform the following steps on the remote server:

1. Create a new user (e.g., devops) with the command:

sudo useradd -m -s /bin/bash devops

(Change the username if necessary)

2. Navigate to `/home/userYouCreated/.ssh`. If `.ssh` directory doesn't exist, create it by running:

mkdir /home/userYouCreated/.ssh


3. Inside the `.ssh` directory, create a file named `authorized_keys` if it doesn't exist.

4. Paste the copied public key into the `authorized_keys` file.

### Configuring SEMAPHORE UI

1. Access SEMAPHORE UI.
2. Navigate to "Add a key store."
3. Choose "New key."
4. Enter the following details:
- Username: The username created on the remote server.
- Type: SSH Key

5. Paste the private key into the provided text area.

### Note

- Ensure that SSH connectivity is established from the machine managing through Ansible SEMAPHORE GUI to the desired remote machine. This step is crucial for adding the remote host's fingerprint to the list.

- In case Docker is used, access the terminal of the SEMAPHORE container, establish SSH connection to the remote host, and the fingerprint will be automatically added.

## Credit: Corr Cloud @ Youtube
