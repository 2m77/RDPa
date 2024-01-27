![image](https://user-images.githubusercontent.com/58414694/149808540-5cfe38ee-a88b-4e8b-a1e9-2a5a1fda7f1d.png)
### GitHub Actions: Windows Ngrok RDP Workflow

🖥️ Automate Windows Remote Desktop setup with ngrok using GitHub Actions!


### RDP code

```
name: CI

on: [push, workflow_dispatch]

jobs:
  build:

    runs-on: windows-latest
    timeout-minutes: 9999

    steps:
    - name: Download
      run: Invoke-WebRequest https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip
    - name: Extract
      run: Expand-Archive ngrok.zip
    - name: Auth
      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN
      env:
        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}
    - name: Enable TS
      run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0
    - run: Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
    - run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1
    - run: Set-LocalUser -Name "admin" -Password (ConvertTo-SecureString -AsPlainText "admin" -Force)
    - name: Create Tunnel
      run: .\ngrok\ngrok.exe tcp 7777

```
###

#### Features:
- **Secure Remote Desktop:** Establish a secure tunnel for remote desktop access to a Windows environment.
- **Ngrok Integration:** Utilize ngrok to create secure tunnels to localhost.
* [+] Super Fast Internet 800MB > 2.5GB !
* [+] Free Linux Storage !
* [+] 8 GB RAM !
* [+] 2 Core GPU !
* [+] Free Life Time !

<br>

#### How to Use:
1. **Fork this repository:** Start by forking this repository to make it your own.
2. **Setup ngrok Auth Token:** Add your ngrok authentication token as `NGROK_AUTH_TOKEN` in your repository secrets.
3. **Customization:** Optionally, tweak any parameters or settings to match your specific Windows environment.

#### Dependencies:
- [ngrok](https://ngrok.com/): A powerful tool for creating tunnels to localhost.

#### Notes:
- This workflow is designed for Windows environments.
- Make sure to check and adjust any firewall or security settings if needed.

Feel free to contribute, share, or customize for your Windows projects! Happy coding! 🚀

## owner
👇👇click here to contact Owner
[![Owner](https://img.shields.io/badge/telegram-blue?style=for-the-badge&logo=telegram)](https://t.me/SH4D0W_X)

💝💝💝💝💝💝💝💝💝💝💝💝💝💝

## Contributing

Feel free to contribute to the project by opening issues, providing feedback, or submitting pull requests. Your contributions are valuable!

## Credits

This project is inspired by [https://t.me/CYB3R_KING].

###                                    THANK YOU