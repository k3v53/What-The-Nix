I have a Wacom Intuos and the following snippet works marvelously
```nix
{config, pkgs , ...}: {
  # Wacom support for x11
  services.xserver.wacom.enable = true;
  environment.systemPackages = [
    # KDE Specific, enables "Graphic Tablet" in "System Settings" 
    pkgs.kdePackages.wacomtablet
  ];
}
```
It's pretty straightforward, tested on x11 and works wonderfully, I will test wayland later on and write here if I have a fix.