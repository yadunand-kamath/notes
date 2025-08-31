## Installation Guide:

1. `pacman -Sy`: Synchronize with the package database.
2. `pacman -S archlinux-keyring`: Updates the keyring (the keyring verifies the authenticity of Arch Linux packages).
3. `archinstall`: Run the installer script.


## Post Installation:

1. `sudo pacman -Syu`: upgrade packages
2. `sudo pacman -S --needed git base-devel`
3. `git clone "AUR-repo-link"`: Clone the AUR repository.
4. `cd <repo-dir>`: Change into the repository's directory.
5. `makepkg -si`: Build the package, resolve dependencies, and install it.
