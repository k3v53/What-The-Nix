Printing in nix is easy, to be honest it felt easier than other distros, you have to enable printing with `services.printing.enable = true;` and with that you have CUPS enabled. You can enable extra functionality described below.
- `services.printing.startWhenNeeded = true;`: This enables the service only when you need to use a printer.
- `programs.system-config-printer.enable = true;` and `services.system-config-printer.enable`: Enables an app that is widely known and used for easy setup of printers in linux desktop.
- [[Avahi]]: `services.avahi`
	- `enable`: Enables discovery of LAN devices (and printers)
	- `nssmdns4`: Enables IPv4 discovery 
	- `openFirewall`: Opens the necessary ports for the protocol to actually work
- `services.printing.drivers`: A list of packages that contains printer drivers, `pkgs.gutenprint` has a lot of printers and will fulfill most users, but you can read about [[NixOS Printer Drivers]] for more info.
# Full Snippet
```nix
  services.printing.enable = true;
  services.printing.startWhenNeeded = true;
  programs.system-config-printer.enable = true;
  services.system-config-printer.enable = true;
  services.avahi = {
    enable = true;
    nssmdns4 = true;
    openFirewall = true;
  };
  services.printing.drivers = [ pkgs.gutenprint ];

```
I recommend to create a [[Lets Modularize Our Configurations (Optional)|module]].
You can customize it even more, read about the other [[attrs]] here: https://search.nixos.org/options?sort=relevance&query=services.printing
# Sources
- I'm not gonna lie, I've read some forums but don't remember the links