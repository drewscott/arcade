This repo contains a collection of bash scripts and libraries used to bootstrap
an arcade system from a fresh Debian 9 (x64).

What do the script do:
* Update the system (`apt-get update`)
* Install and configure plymouth to have a boosplash image
* Create an `arcade` user and auto log it at boot
* Install xorg and start X when `arcade` user log in
* Install alsa audio packages and try to unmutte sound
* Install and configure the Attract-Mode emulator frontend (using packages in
  the `deb/` folder)
* Install and configure MAME (v0.165) to run roms located in
  `/usr/share/arcade/arcade/roms` and using snapshots if present in
  `/usr/share/arcade/arcade/snapshots` (using packages from the `deb/` folder).

# Getting started

## Dependencies

* You **must** have `curl` and `git` installed.
* You **must** have your mame romset for v0.165 in /usr/share/arcade/arcade/roms
* You **can** have your mame games snapshots in /usr/share/arcade/arcade/snapshots

## Clone the repository

```
git clone https://github.com/drewscott/arcade.git
cd arcade
```

## Build missing packages

We will need some missing packages in the `deb/` directory in order to continue
the installation.

### SFML2

[SFML](http://www.sfml-dev.org/index.php) is a multimedia library needed by
the [Attract-Mode](http://attractmode.org/) frontend.

Build the SFML2 debian package using vagrant: `vagrant up build_sfml_packages`.
You should now have the `libsfml_2.5.1_amd64.deb` amd `libsfml-dev_2.5.1_amd64.deb`
packages in the `deb/` repository.

### Attract-Mode

[Attract-Mode](http://attractmode.org/) is an emulator frontend.

Build the Attract-Mode debian package using vagrant:
`vagrant up build_attract_package`.
You should now have the `attract-mode_2.5.1_amd64.deb` package in the `deb/`
repository.

### MAME

[MAME](http://mamedev.org/) is an arcade machine emulator.

Build the MAME debian package using vagrant: `vagrant up build_mame_package`.
You should now have the `mame_0.165_amd64.deb` package in the `deb/` repository.

## Bootstrap

**As root (or using sudo)** start the `./bootstrap` script to install and
configure everything.

# Artwork

* Bootloader image: [Bad Company by Kaiseto](http://kaiseto.deviantart.com/art/Bad-Company-128055448)
