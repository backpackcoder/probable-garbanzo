# probable-garbanzo
Server configuration for my domain docker server

## Server setup
The server setup is baased off a vanila Ubuntu 16.04.1 LTS server setup.
The following additional software has been installed.

### Configuration files
Copy all system configuration files are located under the `filesystem`
directory which corresponds to the root `\` of ther filesystem on the
server.

### Docker
The instruction below are compiled from the [Docker Documentation](https://docs.docker.com/engine/installation/linux/ubuntulinux/)

```bash
echo "Updating apt to use correct Docker repository"
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
sudo apt-get update
sudo apt-get purge lxc-docker
apt-cache policy docker-engine

echo "Updating recommended packages"
sudo apt-get install linux-image-extra-$(uname -r)
```

Reboot your system now.

```bash
echo "Installing docker"
sudo apt-get update
sudo apt-get install docker-engine
sudo service docker start

echo "Adding current user to docker group"
sudo groupadd docker
sudo usermod -aG docker $USER

docker version
```
You should see the docker version for the client and server.

```bash
echo "Setting docker and containers to start on boot"
sudo systemctl enable docker
sudo systemctl enable docker-website
sudo systemctl enable docker-wif
```
