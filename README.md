# ansible-valt-encrypted-env
Pet-project with utility which helps you to implement safe environment variables on dedicated Linux machine.
## Problem
Curent pet-project solves following problem:
You have infrastructure unit which is accessible for other people by root-access. It's common story about DEV-environment in infrastructure teams.
For example, you want to use terraform from your working machine in dev-environment that makes you defining environment variables with tokens, http-auth etc.
You can't define these environment variables inside ~/.bashrc file because it other root-access users can read this file without any problem.

## Solution
You can store some env file. Default for current project is `~/.env.sh` that contains shell script with environment variables setting.
Then you can use:
```shell
ansible-vault encrypt ~/.env.sh # You can write down your own path to this file
```
Vault will ask your password.
Then you can store code that decrypts (using `ansible-vault view ~/.env.sh` command) this file asking password on system log in inside your `~/.bashrc` file.

## Automation
It's not neccessary to install ansible-vault and configure your ~/.bashrc file by hands.
Use `./bashrc_modifier.sh` to modify your `~/.bashrc` content with small necessary code.

