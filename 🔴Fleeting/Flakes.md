# Flakes

- a wrapper around other nix configurations
	- provides a `flakes.lock` file that ensures version locking
	- overall increases reproducibility
- <mark style="background: #FF5582A6;">Currently an experimental feature</mark>
	- basicly also requires the experimental "new CLI" `nix-command`

```nix
# in the configuration.nix
nix.settings.experimental-features = [ "nix-command" "flakes" ];
```

```bash
# get templates
nix flake show templates
nix flake init -t templates#full 
```


## Inputs

https://nixos-and-flakes.thiscute.world/other-usage-of-flakes/inputs
- completely replaces `nix-channel` with the `inputs` section in `flake.nix`
- defines all the dependencies of the flake

```nix
inputs = { 
	# NixOS official package source, using the nixos-24.11 branch here
	nixpkgs.url = "github:NixOS/nixpkgs/nixos-24.11";
};
```



---

Origin: 
References: [[NixOS]]
Tags: 
Created: 11.02.2025

