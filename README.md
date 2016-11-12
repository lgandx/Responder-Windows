# Responder And MultiRelay For Windows #

NBT-NS/LLMNR Responder and Cross-Protocol NTLM Relay Windows Version (Beta)

Laurent Gaffie <laurent.gaffie@gmail.com>

http://g-laurent.blogspot.com/

Follow Responder latest updates on twitter:

https://twitter.com/PythonResponder

## Intro ##

This tool is first an LLMNR, NBT-NS and MDNS responder, it will answer to 
*specific* NBT-NS (NetBIOS Name Service) queries based on their name 
suffix (see: http://support.microsoft.com/kb/163409). By default, the
tool will only answers to File Server Service request, which is for SMB.
The concept behind this, is to target our answers, and be stealthier on
the network. This also helps to ensure that we don't break legitimate
NBT-NS behavior. You can set the -r option via command line if 
you want this tool to answer to the Workstation Service request name
suffix.

MultiRelay has also been ported to this Windows version, allowing a pentest to pivot across compromises.

## Features ##

- Experimental Windows Version.

- Goal of this version is to be able to propagate compromises across subnets and domains from any compromised Windows machine. This tool can also be used compromise a domain from an external penetration test.

- This version will disable netbios on all interfaces and the current firewall profile on the target host.

- Default values will be turned back On when killing Responder (CRTL-C).

- LLMNR and Netbios works out of the box on any Windows XP-2003 and apparently on Windows 2012/2016.

- Netbios support works on all versions.

- Best way to collect hashes with this Windows version: Responder.exe -i IP_Addr -rPv

## Installing ##

- Binary:

Just drop the executable and the configuration file (Responder.conf) inside a directory (eg: c:/temp/responder) and launch it.

- From source: 
Install python on a Windows machine.

run "pip install pyinstaller"

cd in Responder source directory

pyinstaller --onedir -F Responder.py

cd tools/MultiRelay/

pyinstaller --onedir -F MultiRelay.py

Your binary will be located in the folder dist/

- Executing the source directly:

You can run Responder as usual from the source folder (with python installed): python Responder.py 

## Considerations ##

- Make sure a conventional Responder.conf file is present in Responder running directory.

- Any rogue server can be turn off in Responder.conf.

- For now, SMB rogue authentication server is *not* supported in Responder and MultiRelay.

## Donation ##

You can contribute to this project by donating to the following BTC address:

1Pv9rZMNfy9hsW19eQhNGs22gY9sf6twjW


## Copyright ##

NBT-NS/LLMNR/MDNS Responder
Created and maintained by Laurent Gaffie
 
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
 
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>

