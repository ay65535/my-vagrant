# My Vagrant/PuPHPet Default Setup
---
## Setup
---
- Install vagrant on your system see [vagrantup.com](http://vagrantup.com/v1/docs/getting-started/index.html)

- Setup dnsmasq see [Dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html)
  - Alternative to dnsmasq is to configurate your `hosts` file instead.

- Get a copy of this repository. You can do this either by integrating it as a git submodule or by just checking it out and copying the files.

- Copy `puphpet/config.yaml` to `puphpet/config-custom.yaml` and modify `puphpet/config-custom.yaml` according to your needs.    
  Example:  
  ```yaml
  # Custom box configurations.  
  vagrantfile-local:
    vm:
      hostname: 'symfony.dev'
      network:
        private_network: 192.168.50.4
    ssh:
      forward_agent: true
    apache:
      vhosts:
        custom-site:
          servername: symfony.dev
  ```

- Setup dnsmasq or your `hosts` file for the selected `hostname` and `ip` set in `puphpet/config-custom.yaml`.

- Git clone your project to a folder `www/web` or whatever suit your needs. Just remember to setup `puphpet/config-custom.yaml`, so it points to the right folder under apache or nginx configurations.

- Execute "vagrant up" in the directory.

## Infrastructure
---
After performing the steps listed above, you will have the following environment set up:

- A running virtual machine with your project on it
- The folder `www` will be mounted as a shared folder in this virtual machine at `/srv`