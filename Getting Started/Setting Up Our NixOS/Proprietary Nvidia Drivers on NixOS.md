---
aliases:
  - Nvidia Drivers
  - ../../Getting-Started/Setting-Up-Our-NixOS/Nvidia-Drivers-on-NixOS
  - /Nvidia-Drivers
difficulty: "1"
---

NixOS has one of the most straightforward ways of installing these drivers, you have to include this in your [[configuration.nix]] or create a new module
```nix
  # Allow unfree packages
  nixpkgs.config.allowUnfree = true;
  # Load nvidia driver for Xorg and Wayland
  services.xserver.videoDrivers = [ "nvidia" ];
  # Enable OpenGL
  hardware.opengl = {
    enable = true;
  };
  hardware.nvidia = {
    package = config.boot.kernelPackages.nvidiaPackages.production;

    # Modesetting is required.
    modesetting.enable = true;

    # Nvidia power management. Experimental, and can cause sleep/suspend to fail.
    # Enable this if you have graphical corruption issues or application crashes after waking
    # up from sleep. This fixes it by saving the entire VRAM memory to /tmp/ instead 
    # of just the bare essentials.
    powerManagement.enable = false;

    # Fine-grained power management. Turns off GPU when not in use.
    # Experimental and only works on modern Nvidia GPUs (Turing or newer).
    powerManagement.finegrained = false;

    # Use the NVidia open source kernel module (not to be confused with the
    # independent third-party "nouveau" open source driver).
    # Support is limited to the Turing and later architectures. Full list of 
    # supported GPUs is at: 
    # https://github.com/NVIDIA/open-gpu-kernel-modules#compatible-gpus 
    # Only available from driver 515.43.04+
    # Currently alpha-quality/buggy, so false is currently the recommended setting.
    open = false;

    # Enable the Nvidia settings menu,
    # accessible via `nvidia-settings`.
    nvidiaSettings = true;
  };
```

This snippet has the stable nvidia drivers package and the recommended settings for a desktop nvidia gpu to work.
## What does allowUnfree means?
`nixpkgs.config.allowUnfree = true;`: Enables support for non-free software, it is necessary here because we are looking for the official proprietary drivers.
## Laptops
I don't have a laptop so I can't continue writing about them but feel free to read the unofficial wiki: https://nixos.wiki/wiki/Nvidia#Laptop_Configuration:_Hybrid_Graphics_.28Nvidia_Optimus_PRIME.29.
If you have one and want to make a contribution to this entry feel free to do it!
# Source
- Forums that i don't remember the link
- https://nixos.wiki/wiki/Nvidia