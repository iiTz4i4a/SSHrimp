# SSHrimp

<p align="center">
  A simple and convenient CLI tool for managing and connecting to your SSH hosts.
</p>

---

## Navigation

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Interactive Menu](#interactive-menu)
  - [Direct Connection](#direct-connection)
- [Configuration](#configuration)
- [Security Warning](#security-warning)

---

## Features

- **Interactive Menu**: A user-friendly, pseudo-graphical interface for managing SSH connections.
- **Connection History**: Saves your SSH connections for quick access.
- **Multiple Authentication Methods**: Supports password, and SSH key authentication.
- **Direct Connection**: Connect directly to a host by providing the connection string as an argument.
- **Connection Management**: Easily add, remove, and rename your saved connections.
- **Port Selection**: Specify a port for your SSH connections.

## Prerequisites

Before using this script, you may need to install `sshpass` if you plan to use password-based authentication.

### Installing `sshpass`

- **On Debian/Ubuntu:**
  ```bash
  sudo apt-get update
  sudo apt-get install sshpass
  ```

- **On Fedora/CentOS/RHEL:**
  ```bash
  sudo dnf install sshpass
  # or
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
    git clone https://github.com/iiTz4i4a/SSHrimp.git
    cd SSHrimp
    ```

2.  **Make the script executable:**
    ```bash
    chmod +x sshrimp
    ```

3.  **Make the script accessible from any directory (choose one of the following methods):**

    - **Method 1: Move to a directory in your PATH (recommended)**

      Move the `sshrimp` script to a directory that is in your system's `PATH`. A common choice is `/usr/local/bin`.

      ```bash
      sudo cp sshrimp /usr/local/bin/
      ```
      Now you can run the script by simply typing `sshrimp` in your terminal.

    - **Method 2: Create an alias**

      Add an alias to your shell's configuration file (e.g., `~/.bashrc`, `~/.zshrc`).

      ```bash
      echo "alias sshrimp='$(pwd)/sshrimp'" >> ~/.bashrc
      source ~/.bashrc
      ```
      *(Replace `~/.bashrc` with `~/.zshrc` if you are using Zsh)*

## Usage

### Interactive Menu

To open the interactive menu, run the script without any arguments:

```bash
sshrimp
```

You will be presented with a menu where you can:
- **Select a saved connection to connect.**
- **(a) Add a new connection:**
    - Provide an alias, username, host, and port.
    - Choose an authentication method: password or SSH key.
- **(r) Remove a saved connection.**
- **(e) Rename a saved connection.**
- **(q) Quit.**

### Direct Connection

You can also connect to a host directly.

**By Connection String:**

Provide a connection string in the format `user@host:port`.

```bash
sshrimp user@hostname:2222
```
If the port is not specified, it will default to port `22`.

**With an SSH Key:**

Use the `-i` flag to specify the path to your SSH key.

```bash
sshrimp user@hostname -i /path/to/your/key
```

If the connection is new, the script will prompt you for an alias and authentication details (if not already provided), and then save the connection for future use.

## Configuration

The script stores connection details in a file in your home directory: `~/.ssh_connections`. Each line in this file represents a connection and is formatted as follows:

```
alias|username|host|password|port|key_path
```

## Security Warning

**⚠️ Important:** When using password authentication, this script stores SSH passwords in plain text in the `~/.ssh_connections` file. This is a security risk. Use this script only in a secure environment and at your own risk. **For better security, it is highly recommended to use SSH keys instead of passwords.**
