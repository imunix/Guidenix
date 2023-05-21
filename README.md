# Guidenix
"A minimal guide to setting up a hardened NixOS machine, including essential applications and tools to enhance your NixOS experience. While it may not cater to everyone's needs, it offers decent solutions for both new and intermediate NixOS users."

## Activating the firewall:

NixOS comes with a simple, stateful firewall that blocks incoming connections and other unexpected packets and is enabled by adding the following line to your system configuration.
```
networking.firewall.enable = true;
```
In case you want to open ports occasionally and do it with comfort and have no open ports as a default, you can add the following lines:
```
  networking.firewall.allowedTCPPorts = [];
  networking.firewall.allowedUDPPorts = [];
 ```
 
 
# Activating the outbound firewall
In case you worry about things calling home, you could use an outbound firewall.
Opensnich is a program capable of filtering outgoing packets.
To install and configure Opensnitch on your system, you can paste the following code into your system configuration.
```
#  services.opensnitch.enable = true;
```


## Sandboxing Applications by running them inside a VM

Running applications inside a virtual machine adds several layers of added security.
Appvm is a program that enables us to run applications within a hypervisor based sandbox which uses the nix package manager.
Appvm uses a single read-only nix directory for all appvms so spinning up a new appvm is quick.
#### Installing Appvm
To install and configure appvm on your system you can paste the following code into your system configuration.

```
services.virtualisation.appvm = {
  enable = true;
  user = "your-username";
};
```


#### To search for an application 
```
$ appvm search chromium
```
#### Running an application
```
$ appvm start chromium
```
