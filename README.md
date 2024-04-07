# VPS FLUKJOKREX
<h1>การใช้งานเครื่องเหมือน GITHUB </h1>
# 1. GITHUB สร้างที่เก็บข้อมูล ตั้งชื่อ ....
สร้าง file = .github/workflows/main.yml



#######################################################
-----------------------------------------------------
{}ไม่เกี่ยว
COPPY : name: ci =    run: .\ngrok\ngrok.exe tcp 3389

{ coppy -----

name: CI

on: [push, workflow_dispatch]

jobs:

  build:

    runs-on: windows-latest

    steps:

    - name: Download

      run: Invoke-WebRequest https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-windows-amd64.zip -OutFile ngrok.zip

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

    - run: Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "P@ssw0rd!" -Force)

    - name: Create Tunnel

      run: .\ngrok\ngrok.exe tcp 3389 }
      ################################
      ----------------------------------------------------

      # การใช้โทเคน ลง Github 
1.ที่เก็บข้อมูล ของคุณ 
2. ไปที่ ตั้งค่า secrets and variables -Actions secrets and variables
3. ใน Actions secrets and variable  - Repository secrets 
4. new Repository secrets ตั้งชื่อ NGROK_AUTH_TOKEN
5. new Repository secrets - Value ให้ใส่ token = ngrok.com




      
