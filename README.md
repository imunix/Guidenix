# Guidenix
## "A minimal guide to setting up a hardened NixOS machine, including essential applications and tools to enhance your NixOS experience. While it may not cater to everyone's needs, it offers decent solutions for both new and intermediate NixOS users."

## Sandboxing Applications by running them inside a VM

Running applications inside a virtual machine adds several layers of added security.
Appvm is a program that enables us to run applications within a hypervisor based sandbox which uses the nix package manager.
Appvm uses a single read-only nix directory for all appvms so spinning up a new appvm is quick.
#### Installing Appvm
To install and configure appvm on your system you can paste the following code into your system configuration.

services.virtualisation.appvm = {
  enable = true;
  user = "your-username";
};

#### To search for an application 

$ appvm search chromium

#### Running an application
$ appvm start chromium

