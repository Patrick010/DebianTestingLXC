# Debian Testing LXC Template for Proxmox

This is a minimal Debian **testing** LXC template for Proxmox VE, built by upgrading the official `debian-12-standard_12.7-1_amd64.tar.zst` container to the current `testing` release.

## Features

- Based on official Proxmox Debian 12 template  
- Upgraded to Debian testing (rolling release)  
- Cleaned, trimmed, compressed with zstd  
- No cloud-init, no unnecessary packages  
- Logs, docs, locales, APT cache stripped  
 
## Usage

Because of the max 100MB filesize limit imposed by Github I had to upload the template to archive.org.

1. Download the template https://archive.org/download/debian-testing-amd64.tar/debian-testing-amd64.tar.zst

2. Upload the `.tar.zst` file to your Proxmox node:

   ```
   /var/lib/vz/template/cache/
   ```

3. Create a container from the template from the Proxmox UI, or by using this commandline:

   ```bash
   pct create <vmid> local:vztmpl/debian-testing-amd64.tar.zst --rootfs local-lvm:8 --hostname my-ct
   ```

   Adjust `<vmid>`, storage, and hostname as needed.

## ⚠️ Notes

- Compressed with `zstd -19 --long=27` for Proxmox compatibility  
- You can customize further after container creation  
- This is not an official template — use at your own discretion

## Build Info

Built manually in a chroot using the following steps:

- Extracted base Proxmox Debian 12 LXC template
- Chrooted and upgraded to testing via `apt full-upgrade`
- Cleaned system and compressed to `.tar.zst`

---
License

This script is provided as-is under the GPL-3.0 License. See LICENSE file for details.

Feel free to customize and report issues or change requests.
