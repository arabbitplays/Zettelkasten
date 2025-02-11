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

- completely replaces `nix-channel` with the `inputs` section in `flake.nix`

---

Origin: 
References: [[NixOS]]
Tags: 
Created: 11.02.2025

