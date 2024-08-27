If you tried to use a hostname from another computer or your own computer has problems when trying to get connections from outside, this could help you.
Add in your [[configuration.nix]] the following code:
```nix
services.avahi.enable = true;
services.avahi.openFirewall = true;
services.avahi.nssmdns4 = true;
```
- TODO: Pending explanation...
# Sources
- https://discourse.nixos.org/t/help-with-local-dns-resolution/20305/6