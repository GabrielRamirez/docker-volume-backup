# docker-volume-backup

`docker-volume-backup` is a simple command-line tool to back up and restore Docker volumes. It allows you to create backups of Docker volumes, restore them from backup files, and manage your Docker volumes with ease.

## Features
- **Backup Docker volumes**: Backup all or specific volumes to a local directory.
- **Restore Docker volumes**: Restore a volume from a backup file.
- **List Docker volumes**: List all available Docker volumes.
- **Logging**: Optional logging for debugging and tracking operations.
  
## Requirements
- Docker installed on your machine.
- Linux-based environment (though it could work on macOS or WSL on Windows with some tweaks).

## Installation

1. **Clone the repository**:
   Clone the `docker-volume-backup` repository to your local machine.

   ```bash
   git clone https://github.com/GabrielRamirez/docker-volume-backup.git
   cd docker-volume-backup
   ```

2. **Make the script executable**:
   Give the `dockup` script execution permissions:

   ```bash
   chmod +x dockup
   ```

3. **(Optional) Move `dockup` to a global location**:
   To make the `dockup` command available globally on your system, copy it to `/usr/local/bin`:

   ```bash
   sudo cp dockup /usr/local/bin/
   ```

   This allows you to run `dockup` from anywhere in the terminal.

## Usage

### Commands:
1. **Backup Docker Volumes**:
   Backup all volumes or specific volumes to a designated backup directory.

   - **Backup all volumes**:
     ```bash
     dockup backup -a --backup-dir=/path/to/backup
     ```

   - **Backup specific volumes**:
     ```bash
     dockup backup -name volume1,volume2 --backup-dir=/path/to/backup
     ```

2. **Restore a Docker Volume**:
   Restore a volume from a backup file.

   - **Restore a specific volume**:
     ```bash
     dockup restore --restore-file=/path/to/backup/volume_backup.tar.gz -name volume1
     ```

3. **List Docker Volumes**:
   List all Docker volumes on your system.

   ```bash
   dockup list
   ```

### Options:

- **Backup**:
  - `-a` – Backup all Docker volumes.
  - `-name <volumes>` – Backup specific volumes (comma-separated).
  - `--backup-dir=<path>` – Specify the backup directory where the backups will be stored.
  - `--verbose` – Enable verbose logging.
  - `--log-file=<path>` – Specify a log file for logging.
  - `--enable-logs` – Enable logging to the specified file.

- **Restore**:
  - `--restore-file=<path>` – Specify the backup file to restore from.
  - `-name <volume>` – Specify the name of the volume to restore.

- **Other**:
  - `--help` – Show the help message.
  - `--version` – Show the script version.

### Example Use Cases

- **Backup all Docker volumes**:
  ```bash
  dockup backup -a --backup-dir=/backups/docker_volumes
  ```

- **Backup specific volumes**:
  ```bash
  dockup backup -name volume1,volume2 --backup-dir=/backups/docker_volumes
  ```

- **Restore a volume from a backup**:
  ```bash
  dockup restore --restore-file=/backups/docker_volumes/volume1_backup.tar.gz -name volume1
  ```

- **List all Docker volumes**:
  ```bash
  dockup list
  ```

## Logging

You can enable logging by passing the `--enable-logs` option, which will log all operations to a file. If the `--log-file` option is not provided, logs will be written to the default location (`/var/log/dockup`).

## Contributing

If you'd like to contribute to `docker-volume-backup`, feel free to open an issue or submit a pull request. We welcome any improvements or bug fixes!

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

## Author

- [Gabriel Ramirez](https://github.com/GabrielRamirez)