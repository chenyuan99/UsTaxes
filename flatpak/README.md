# UsTaxes Flatpak

This directory contains the necessary files to build UsTaxes as a Flatpak package and submit it to Flathub.

## Building the Flatpak Locally

To build and install the Flatpak locally, follow these steps:

### Prerequisites

1. Install Flatpak and flatpak-builder:

```bash
# For Fedora
sudo dnf install flatpak flatpak-builder

# For Ubuntu/Debian
sudo apt install flatpak flatpak-builder

# For Arch Linux
sudo pacman -S flatpak flatpak-builder
```

2. Add the Flathub repository:

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

3. Install the required SDK and runtime:

```bash
flatpak install flathub org.freedesktop.Platform//23.08 org.freedesktop.Sdk//23.08 org.freedesktop.Sdk.Extension.node20 org.freedesktop.Sdk.Extension.rust-stable
```

### Building the Flatpak

From the root directory of the UsTaxes repository:

```bash
flatpak-builder --force-clean build-dir com.ustaxes.UsTaxes.yml
```

### Testing the Flatpak

To run the built Flatpak:

```bash
flatpak-builder --run build-dir com.ustaxes.UsTaxes.yml ustaxes
```

### Installing the Flatpak Locally

To install the built Flatpak:

```bash
flatpak-builder --install --force-clean build-dir com.ustaxes.UsTaxes.yml
```

Then you can run it with:

```bash
flatpak run com.ustaxes.UsTaxes
```

## Submitting to Flathub

To submit UsTaxes to Flathub:

1. Fork the [flathub/flathub](https://github.com/flathub/flathub) repository
2. Create a new branch
3. Create a directory named `com.ustaxes.UsTaxes` and add the manifest file and any other necessary files
4. Submit a pull request to the Flathub repository

For more detailed instructions, see the [Flathub documentation](https://docs.flathub.org/docs/for-app-authors/submission/).

## Updating the Flatpak

When a new version of UsTaxes is released, update the following:

1. Update the version number in the `releases` section of `com.ustaxes.UsTaxes.metainfo.xml`
2. If necessary, update dependencies in the `com.ustaxes.UsTaxes.yml` manifest
