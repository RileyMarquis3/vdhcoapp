# DownloadHelper CoApp - Troubleshooting

If the coapp is not recognised by the extension, here are a few things you can try:

- Try the latest coapp. You will find the download links [here](https://www.downloadhelper.net/install-coapp-v2).
- If you use Edge, make sure to install the addon from the Microsoft store, not the Google store. See relevant links [here](https://www.downloadhelper.net/install).

## Windows Antivirus

It's possible that your Antivirus blocks the CoApp. Sadly, Antivirus can be overly protective. Our application is OpenSource, and not malicious in any way, you can look at the source code [right here](https://github.com/aclap-dev/vdhcoapp). Video Downloadhelper has been validated by Google, Microsoft and Mozilla organizations. We recommend either:

- using the [Microsoft Antivirus](https://www.microsoft.com/en-us/windows/comprehensive-security) - it is free and [recommended by Microsoft](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/why-use-microsoft-defender-antivirus?view=o365-worldwide);
- or allowing the CoApp (you'll need to allow the 3 ".exe" files located in the installation directory).

## Windows Installation Error

If you're getting an error during installation, try installing after closing your browser (Firefox, Chrome, Edge).

## Windows 7

We have dedicated builds for Windows 7. You will find the download links [here](https://www.downloadhelper.net/install-coapp-v2). **Make sure to install the Windows 7 version** (_vdhcoapp-xxx-win7-x86_64-installer.exe_).

## Mac

After install, start the coapp (only one time after intallation), this should re-register the app in the relevant browsers.
If you use an old version of MacOS, [see this](https://github.com/aclap-dev/vdhcoapp/issues/190).

## Ubuntu (and Flatpak / Snap based systems)

Most of the time, the issue is a missed prompt. Firefox should have showed you a prompt to allow the coapp to communicate with the extension. Some people miss the prompt, or the prompt just never shows up. There's no user interface to change that setting. To solve this, run these commands (even if you don't use Flatpak):

```
sudo apt-get install -y flatpak
flatpak permission-set webextensions net.downloadhelper.coapp snap.firefox yes
```

## Firejail-based systems

See this [comment](https://github.com/aclap-dev/vdhcoapp/issues/189#issuecomment-1888447688).

## KDE Neon (and AppArmor based systems)

Add `/opt/vdhcoapp/vdhcoapp ux,` to `/etc/apparmor.d/local/usr.bin.firefox`.

Then restart *apparmor.service* and *Firefox*.

## Linux (all)

- Run `/opt/vdhcoapp/vdhcoapp install` (**not as root! Don't use sudo**) to re-register the app.
- Move to the installation folder of the coapp in your terminal, and run: `/opt/vdhcoapp/vdhcoapp --info`. It will run some diagnostic operations.
- do not install vdhcoapp within the `/usr/` directory, it won't be detected by your browser. [See here why](https://github.com/aclap-dev/vdhcoapp/issues/160#issuecomment-1780765719).
- **Snap Chromium-based browsers**: they do not support native messaging yet. It is up to Google to fix this issue.