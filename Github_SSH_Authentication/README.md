# GitHub Authentication

## HTTPS

- password authentication depreciated, need to use personal access token now.

## SSH

- Can generate private-public SSH keypair and store public key on GitHub profile.
- Use private key SSH authentication for all GitHub repos.

![GitHub SSH Authentication](../images/ssh_github_authentication.avif)

### Steps to Use SSH Authentication with GitHub

1. **Generate an SSH Key Pair**:

    - cd into your ssh folder

    ```bash
    cd ~/.ssh
    ```

    - run the command below to generate new SSH key pair.
  
     ```bash
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     ```

    - Specify key name e.g. `yourname_github_key`. Leave passphrase empty.
    - Should see a .pub (public key) and a private key generated, with the name specified.

2. **Add the Private SSH Key to the SSH Agent**:

   - Start the SSH agent in the background.
  
     ```bash
     eval `ssh-agent -s`
     ```

   - Add your SSH private key to the SSH agent.
  
     ```bash
     ssh-add ~/.ssh/<private_key_name>
     ```

3. **Add the Public SSH Key to Your GitHub Account**:

   - Copy the SSH public key to your clipboard:

     ```bash
     pbcopy < ~/.ssh/<public_key_name>
     ```

   - Go to GitHub, navigate to **Settings** > **SSH and GPG keys**, and click **New SSH key**.
   - Paste the SSH public key into the "Key" field and give it a descriptive title.

4. **Test SSH Authentication to GitHub**

    - Run the command below to test if the connection is successful.

    ```bash
    ssh -T git@github.com
    ```

5. **Clone Repositories Using SSH**:

   - Use the SSH URL to clone repositories.
  
     ```bash
     git clone git@github.com:username/repository.git
     ```

   - If this is successful, which it should be if the test connection command succeeded, then you have used SSH to authenticate with GitHub. This bypasses the need to enter username and password (deprecated) for HTTPS.