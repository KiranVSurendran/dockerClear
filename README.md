# Docker Cleanup Guide

This guide provides all possible ways to delete Docker components, including images, containers, volumes, and networks.

## 1. Remove All Containers
To remove all running and stopped containers:
```sh
docker rm -f $(docker ps -aq)
```

To remove only stopped containers:
```sh
docker container prune -f
```

## 2. Remove All Images
To delete all Docker images:
```sh
docker rmi -f $(docker images -aq)
```

To remove unused images:
```sh
docker image prune -a -f
```

## 3. Remove All Volumes
To delete all Docker volumes:
```sh
docker volume rm $(docker volume ls -q)
```

To remove unused volumes:
```sh
docker volume prune -f
```

## 4. Remove All Networks
To delete all Docker networks:
```sh
docker network rm $(docker network ls -q)
```

To remove unused networks:
```sh
docker network prune -f
```

## 5. Remove Everything (Containers, Images, Volumes, Networks)
To completely wipe out all Docker components:
```sh
docker system prune -a --volumes -f
```

## 6. Remove Docker Completely
To remove Docker entirely from the system:
```sh
sudo systemctl stop docker
sudo apt-get remove --purge -y docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker /etc/docker
```
(For non-Debian-based systems, use the appropriate package manager.)

## 7. Additional Cleanup
To remove dangling build cache:
```sh
docker builder prune -a -f
```

To ensure all processes are stopped:
```sh
sudo systemctl stop docker
```

## 8. Ubuntu Space Check and Cleanup
To check disk usage:
```sh
df -h
```

To find the largest files and directories:
```sh
sudo du -ah / | sort -rh | head -n 20
```

To clean up space:
- Remove unnecessary log files:
  ```sh
  sudo journalctl --vacuum-size=100M
  ```
- Clean up package cache:
  ```sh
  sudo apt-get autoremove -y && sudo apt-get clean
  ```
- Remove old kernels:
  ```sh
  sudo apt-get autoremove --purge
  ```
- Delete large unnecessary files manually:
  ```sh
  sudo rm -rf /path/to/large/file
  ```

This guide covers all major cleanup options for Docker and Ubuntu. Use these commands with caution as they permanently delete data.

