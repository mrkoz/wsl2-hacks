# WSL Hacks

Built for a hybrid windows/wsl environment.

First up, clone this repo to somewhere that can be found in bash and in Windows and update the `vpn.sh` file to match your file path.

## WSL basic config

`wsl.conf` runs inside your WSL install, create a file with the same contents (tweak it if you wish) in `/etc/wsl.conf`.
`.wslconfig` should be in your windows `~` dir

## Bash profile

```bash
# Bring in the VPN bash functions
source path-to-your/wsl2-hacks/vpn.sh

# We've killed the windows paths I've created some aliases to bring back in some apps I use
_USER=$(/c/Windows/System32/cmd.exe /c 'echo %USERNAME%' | sed -e 's/\r//g')
alias wsl.exe='/c/windows/system32/wsl.exe'
alias powershell.exe='/c/windows/System32/WindowsPowerShell/v1.0//powershell.exe '
alias explorer.exe='/c/windows/explorer.exe'
alias code="/c/Users/${_USER}/AppData/Local/Programs/Microsoft\ VS\ Code/bin/code"

```

## VPN hacks

the `vpn.sh` file updates the metric for the VPN when you call:

Manual steps are required;

in bash call `vpn_on`  when you connect and `vpn_off` when youdisconnect from the VPN



I followed [this thread](https://github.com/microsoft/WSL/issues/1350#issuecomment-742518507) to figure this part out

it uses a mix of powershell and bash, don't forget to update the `vpn.sh` file to match your routable path to the powershell script.