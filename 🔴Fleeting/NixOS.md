# NixOS


- Nix is a declarative package manager and a programming language
	- makes it possible to define most of the system state via one configuration file
- NixOS is a Linux distribution build on top of Nix
	- Keeps older states as long as needed so its always possible to roll back

- the default configuration file is `/etc/nixos/configuration.nix`
	- describes the whole system in a reproducible manner
	- apply the configuration with `sudo nixos-rebuild switch`
	- relies on data sources by `nix-channel` and has no version-locking mechanism
		- better alternative is [[Flakes]]

- <mark style="background: #FFB86CA6;">Nix-channel</mark>
	- manages software package versions

---

Origin: https://nixos-and-flakes.thiscute.world/introduction/
References: 
Tags: 
Created: 11.02.2025

