> [!info] From Manpage
> This command updates the system so that it corresponds to the configuration specified in /etc/nixos/configuration.nix or /etc/nixos/flake.nix. Thus, every time you modify the configuration or any other NixOS module, you must run **nixos-rebuild** to make the changes take effect. It builds the new system in /nix/store, runs its activation script, and stop and (re)starts any system services if needed. Please note that user services need to be started manually as they aren't detected by the activation script at the moment.

# Sources
- https://www.mankier.com/8/nixos-rebuild
- https://nixos.wiki/wiki/Nixos-rebuild