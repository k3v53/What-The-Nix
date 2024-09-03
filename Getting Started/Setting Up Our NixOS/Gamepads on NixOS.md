---
aliases:
  - Wired Gamepads on NixOS
  - Wireless Gamepads on NixOS
---

# Wired Gamepads


Wired Gamepads should work out of the box, but there are some others that need extra work.

# Wireless Bluetooth Gamepads

First of all, enable Bluetooth on your [[configuration.nix]].
```nix
hardware.bluetooth.enable = true;
```

Now do a [[nixos-rebuild switch]], enable Bluetooth and try to pair them.
If you can't pair them because it asks for a pin (and you don't have a way to determine the pin), you have to enable a setting called `ClassicBondedOnly`, you can enable it like this:
```nix
hardware.bluetooth.input = {
  General = {
    ClassicBondedOnly = false;
  };
};
```
This setting works with most generic controllers, PS3, PS4 and Xbox controllers. I've tested them myself and all of them work.

> [!warning]
>If you have been searching on the web and overridden the default bluez package, delete those lines because it is not necessary anymore, only leave the override if you know what are you doing!

If you're lost like I was after writting this page, please read [[Weird Nix Shenanigans Explained]].