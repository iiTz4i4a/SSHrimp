# SSHrimp

This script is a simple and convenient tool for managing and connecting to SSH hosts. It provides an interactive menu for selecting, adding, and removing SSH connections, and supports direct connections.

## Current Banner

```
          _____                    _____                    _____                    _____                    _____                    _____                    _____          
         /\    \                  /\    \                  /\    \                  /\    \                  /\    \                  /\    \                  /\    \         
        /::\    \                /::\    \                /::\____\                /::\    \                /::\    \                /::\____\                /::\    \        
       /::::\    \              /::::\    \              /:::/    /               /::::\    \               \:::\    \              /::::|   |               /::::\    \       
      /::::::\    \            /::::::\    \            /:::/    /               /::::::\    \               \:::\    \            /:::::|   |              /::::::\    \      
     /:::/\:::\    \          /:::/\:::\    \          /:::/    /               /:::/\:::\    \               \:::\    \          /::::::|   |             /:::/\:::\    \     
    /:::/__\:::\    \        /:::/__\:::\    \        /:::/____/               /:::/__\:::\    \               \:::\    \        /:::/|::|   |            /:::/__\:::\    \    
    \:::\   \:::\    \       \:::\   \:::\    \      /::::\    \              /::::\   \:::\    \              /::::\    \      /:::/ |::|   |           /::::\   \:::\    \   
  ___\:::\   \:::\    \    ___\:::\   \:::\    \    /::::::\    \   _____    /::::::\   \:::\    \    ____    /::::::\    \    /:::/  |::|___|______    /::::::\   \:::\    \  
 /\   \:::\   \:::\    \  /\   \:::\   \:::\    \  /:::/\:::\    \ /\    \  /:::/\:::\   \:::\____\  /\   \  /:::/\:::\    \  /:::/   |::::::::\    \  /:::/\:::\   \:::\____\ 
/::\   \:::\   \:::\____\/::\   \:::\   \:::\____\/:::/  \:::\    /::\____\/:::/  \:::\   \:::|    |/::\   \/:::/  \:::\____\/:::/    |:::::::::\____\/:::/  \:::\   \:::|    |
\:::\   \:::\   \::/    /\:::\   \:::\   \::/    /\::/    \:::\  /:::/    /\::/   |::::\  /:::|____|\:::\  /:::/    \::/    /\::/    / ~~~~~/:::/    /\::/    \:::\  /:::|____|
 \:::\   \:::\   \/____/  \:::\   \:::\   \/____/  \/____/ \:::\/:::/    /  \/____|:::::\/:::/    /  \:::\/:::/    / \/____/  \/____/      /:::/    /  \/____/\:::\/:::/    / 
  \:::\   \:::\    \       \:::\   \:::\    \               \::::::/    /         |:::::::::/    /    \::::::/    /                       /:::/    /            \::::::/    /  
   \:::\   \:::\____\       \:::\   \:::\____\               \::::/    /          |::|\::::/    /      \::::/____/                       /:::/    /              \::::/    /   
    \:::\  /:::/    /        \:::\  /:::/    /               /:::/    /           |::| \::/____/        \:::\    \                      /:::/    /                \::/____/    
     \:::\/:::/    /          \:::\/:::/    /               /:::/    /            |::|  ~|               \:::\    \                    /:::/    /                  ~~          
      \::::::/    /            \::::::/    /               /:::/    /             |::|   |                \:::\    \                  /:::/    /                               
       \::::/    /              \::::/    /               /:::/    /              \::|   |                 \:::\____\                /:::/    /                                
        \::/    /                \::/    /                \::/    /                \:|   |                  \::/    /                \::/    /                                 
         \/____/                  \/____/                  \/____/                  \|___|                   \/____/                  \/____/
```

## Features

- **Interactive Menu**: A user-friendly, pseudo-graphical interface for managing SSH connections.
- **Connection History**: Saves your SSH connections for quick access.
- **Direct Connection**: Connect directly to a host by providing the connection string as an argument.
- **Password Management**: Stores passwords for automatic login (see Security Warning).
- **Easy to Use**: Simple and intuitive commands.

## Prerequisites

Before using this script, you need to ensure that `sshpass` is installed on your system. `sshpass` is required for password-based authentication.

### Installing `sshpass`

- **On Debian/Ubuntu:**
  ```bash
  sudo apt-get update
  sudo apt-get install sshpass
  ```

- **On Fedora/CentOS/RHEL:**
  ```bash
  sudo dnf install sshpass
  ```
  or
  ```bash
  sudo yum install sshpass
  ```

- **On Arch Linux:**
  ```bash
  sudo pacman -S sshpass
  ```

- **On macOS (using Homebrew):**
  ```bash
  brew install hudochenkov/sshpass/sshpass
  ```

## Installation

1.  **Clone the repository:**
    ```bash
    git clone git@github.com:iiTz4i4a/SSHrimp.git
    cd SSHrimp
    ```

2.  **Make the script executable:**
    ```bash
    chmod +x connect
    ```

3.  **Make the script accessible from any directory (choose one of the following methods):**

    - **Method 1: Move to a directory in your PATH (recommended)**

      Move the `connect` script to a directory that is in your system's `PATH`. A common choice is `/usr/local/bin`.

      ```bash
      sudo cp connect /usr/local/bin/
      ```

      Now you can run the script by simply typing `connect` in your terminal.

    - **Method 2: Create an alias**

      Add an alias to your shell's configuration file (e.g., `~/.bashrc`, `~/.zshrc`).

      ```bash
      echo "alias connect='$(pwd)/connect'" >> ~/.bashrc
      source ~/.bashrc
      ```

      *(Replace `~/.bashrc` with `~/.zshrc` if you are using Zsh)*

## Usage

### Interactive Menu

To open the interactive menu, run the script without any arguments:

```bash
connect
```

You will be presented with a menu where you can:
- Select a saved connection.
- Add a new connection.
- Remove a saved connection.

### Direct Connection

You can also connect to a host directly by providing a connection string in the format `user@host`:

```bash
connect user@hostname
```

If the connection is new, the script will prompt you for a password and an alias, and then save the connection for future use.

## Configuration

The script stores connection details in a hidden file in your home directory: `~/.ssh_connections`. Each line in this file represents a connection and is formatted as follows:

```
alias|username|host|password
```

## Security Warning

**⚠️ Important:** This script stores SSH passwords in plain text in the `~/.ssh_connections` file. This is a security risk. Use this script only in a secure environment and at your own risk. For better security, it is highly recommended to use SSH keys instead of passwords.

# SSHrimp
