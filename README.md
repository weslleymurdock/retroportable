# RetroPortable

## Briefing

RetroPortable is a versioned guide to building a portable RetroPie console with a Raspberry Pi 3 Model B, an MPI3508 3.5-inch touchscreen, and a USB gamepad. It also references the RetroPie BIOS collection as a separate Git submodule.

## Portable RetroPie Console Tutorial

- **Tutorial version:** 1.0
- **Hardware target:** Raspberry Pi 3 Model B, MPI3508 3.5-inch HDMI touchscreen, USB gamepad

### What you need

- Raspberry Pi 3 Model B with a microSD card (16 GB or larger recommended)
- MPI3508 display and its HDMI/touch connections
- USB gamepad
- A regulated 5 V power bank and cable that can power the Pi and display; use the Pi 3's 2.5 A supply recommendation as a minimum
- A case that fits the components while leaving the Pi ventilated
- Network access for setup

### Build and setup

1. **Install RetroPie.** Download the Raspberry Pi 2/3 image from the [official RetroPie download page](https://retropie.org.uk/download/), write it to the microSD card with Raspberry Pi Imager or another image writer, then boot the Pi and complete its first-run setup.
2. **Connect the display.** Attach the MPI3508 to the Pi following its hardware documentation, including the HDMI and touchscreen connections. Confirm the display is working before fitting the components into the case.
3. **Install the display driver.** From a terminal on the Pi, use the steps documented in [LCDWiki's RetroPie driver repository](https://github.com/lcdwiki/LCD-show-retropie):
   ```sh
   git clone https://github.com/lcdwiki/LCD-show-retropie.git
   chmod -R 755 LCD-show-retropie
   cd LCD-show-retropie
   sudo ./MPI3508-show
   ```
   Check the repository's instructions for compatibility with the RetroPie image in use before running the driver. The installation restarts the Pi.
4. **Configure the gamepad.** Connect the USB gamepad and follow EmulationStation's input-configuration prompts. Map the controls and save the configuration.
5. **Add games and firmware you are entitled to use.** Transfer game files to `~/RetroPie/roms/<system>/` and any required BIOS files to `~/RetroPie/BIOS/`, following the relevant system's RetroPie documentation. Restart EmulationStation to refresh the game list.
6. **Make it portable.** Secure the Pi, screen, and cables in the case without blocking ventilation. Test the complete setup on the power bank before closing the case, and avoid exposed contacts that could short against the enclosure.

### BIOS collection reference

The collection at [`modules/RetroPieBios`](modules/RetroPieBios) is an external submodule. To check it out after cloning this project, run:

```sh
git submodule update --init --recursive
```

The collection contains third-party firmware. Review its [legal disclaimer](https://github.com/archtaurus/RetroPieBIOS#legal-disclaimer) and local laws; only use files you are authorized to use.
