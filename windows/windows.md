# 30 Windows Command Line Cheat Sheet

## A. Opening and Managing Files/Folders

### Always open command prompt in administrator Mode
```cmd
runas /user:Administrator cmd
```

### Hide zip or rar files inside an image
```cmd
copy /b image.extension+folder.zip image.extension
```

### Show all wifi passwords
```cmd
netsh wlan show profile
netsh wlan show profile wifinetwork key=clear | findstr "Key Content"
```

### Get all WiFi passwords at once
```cmd
for /f "skip=9 tokens=1,2 delims=:" %i in ('netsh wlan show profiles') do @if "%j" NEQ "" (echo SSID: %j & netsh wlan show profiles %j key=clear | findstr "Key Content") & echo.
```

### Encrypt files in a folder
```cmd
cipher /E
```

### Save Output of a Command to a File
```cmd
command >> output.txt
```

### Create a batch file for WiFi passwords
```cmd
for /F "tokens=2 delims=:" %a in ('netsh wlan show profile') do @(set wifi_pwd= & for /F "tokens=2 delims=: usebackq" %F IN (`netsh wlan show profile %a key^=clear ^| find "Key Content"`) do @(set wifi_pwd=%F) & echo %a : !wifi_pwd!)
```

### Hide/Unhide a folder from everyone
```cmd
attrib +h +s +r foldername
attrib -h -s -r foldername
```

## B. System Information

### Display detailed system operating and configuration info
```cmd
systeminfo
```

### Remove the Mounted Drive
```cmd
subst /d q:
```

### Securely Copy files between remote hosts
```cmd
scp file.txt root@serverip:~/file.txt
```

### Change the Background and Text color in command prompt
```cmd
color 07 [background:text]
```

### Open CMD inside a windows directory
Type `CMD` in the search bar

### Change the Prompt Text
```cmd
prompt {text}$G
```

### Open Explorer from the windows command prompt
```cmd
explorer.
```

### Reset the Prompt Text
```cmd
prompt
```

### Map a regular folder as a mounted drive
```cmd
subst q: c://filelocation
```

### Change the Title of command prompt window
```cmd
title {stuff}
```

## C. Network

### Curl the Weather
```cmd
curl wttr.in/location
```

### Check Your Public IP Address
```cmd
curl checkip.amazonaws.com
```

### Curl Shortened Links to Figure Out the Destination
```cmd
curl --head --location "https://ntck.co/itprotv" | findstr location
```

### Generate a QR Code
```cmd
curl qrenco.de/https://networkchuck.coffee
```

### Check the Status of a Website
```cmd
curl -IsL http://networkchuck.com/ | findstr ^Location
```

## D. Social Media and ChatGPT

### Check Social Media
```cmd
curl -s https://decapi.me/youtube/latest_video?user=networkchuck
curl -s https://decapi.me/twitter/latest?name=networkchuck
```

### Define a word
```cmd
curl dict.org/d:contretemps
```

### Use ChatGPT in CMD with Curl
```cmd
curl https://api.openai.com/v1/chat/completions -H "Authorization: Bearer YOUR_OPENAI_API_KEY" -H "Content-Type: application/json" -d "{\"model\": \"gpt-3.5-turbo\", \"messages\": [{\"role\": \"user\", \"content\": \"Who is NetworkChuck?\"}]}"
```

### ChatGPT Terminal Emulator Prompt
"I want you to act as a Windows command terminal. I will type commands and you will reply with what the terminal should show. I want you to only reply with the terminal output inside one unique code block, and nothing else. Do not write explanations. Do not type commands unless I instruct you to do so. When I need to tell you something in English I will do so by putting text inside curly brackets {like this}. My first command is pwd."

## E. File and Folder Management

### Visit a website
```cmd
start networkchuck.com
```

### Telnet Telehack.com
```cmd
telnet telehack.com
```

### Delete Temporary Files to Clear Space
```cmd
del /q /f /s %temp%\*
del /s /q C:\Windows\temp\*
```

### History of Commands
```cmd
doskey /history
```

## F. Windows Terminal

### Use Windows Terminal Instead of Command Prompt
1. Download and install Windows Terminal from the Microsoft Store or GitHub
2. Launch Windows Terminal
3. Click on the down arrow icon at the top of the window, next to the plus sign, and select "Settings"
4. In the "Settings" window, find the "defaultProfile" setting and set its value to the GUID of the terminal you want to use as the default (e.g. PowerShell, Command Prompt, or WSL)
5. Save the settings and close the "Settings" window
6. To open a new terminal window, press "Ctrl+Shift+T" or click on the plus sign in the tab bar and select the terminal you want to open

### Open Terminal from Any Folder
Shift-right-click on the folder and select Terminal

### Using Windows Terminal, You Can Drag and Drop Files to the Terminal When You Need the File Location
1. Open Windows Terminal and navigate to the directory where you want to run the command
2. Open File Explorer and locate the file you want to get the location of
3. Drag and drop the file onto the terminal window, and the full file path will be pasted into the terminal at the current cursor position

### Use PowerShell for advanced tasks beyond Command Prompt
PowerShell is a powerful task automation and configuration management framework from Microsoft, consisting of a command-line shell and scripting language. It can perform advanced tasks beyond the capabilities of the Command Prompt.

### Get help from Terminal
```cmd
help
```

---

*This cheat sheet covers essential Windows command line operations for system administration, networking, file management, and productivity tasks.*
