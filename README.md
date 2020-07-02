# Polish Characters in HoldAndPress App for Colemak Layout - Fix
In Colemak keyboard layout there is missing on Polish character in HoldAndPress app. 
Please find below a comprehensive solution.

Original solution unfortunately doesn't work as it was available only for old MacOS distributions
[How to add characters to the press and hold - Apple Stackexchange](https://apple.stackexchange.com/questions/20505/how-to-add-characters-to-the-press-and-hold-character-picker-in-os-x-lion)

The same page contains correct steps. Keep in mind to make them work you need to enable make main volume writeable.
1. Disable System Integrity Protection as detailed in How to turn off rootless in Mac OS X El Capitan - MacWorld
2. Navigate to /System/Library/Input Methods/PressAndHold.app/Contents/PlugIns/PAH_Extension.appex/Contents/Resources/ in the Finder. To go to it quickly, press ⇧⌘G and paste the string in.
3. Find your keyboard plist file. If you are using the English layout, you would be looking at Keyboard-en.plist and if you are using the German layout it would be Keyboard-de.plist. It could have other names as well, depending on your keyboard language.
4. Back this file up by pressing ⌘D. Rename the copy you made to something with "backup" in its name.
5. Open up the original file (without backup in its name) and edit the characters you want to in. After that, save it.
6. Enable System Integrity Protection as detailed in the same page as step 1.

## More Info
https://georgegarside.com/blog/macos/custom-characters-accent-popup-osx/

## Fixed Configuration
Corrected file which includes all Polish characters on 1st place and German characters on 2nd
* [Keyboard-en.plist](https://github.com/witcher451/colemak-fix/blob/master/Keyboard-en.plist)

Corrected file which simply modifies original file by adding ‘ą’, ‘Ą’ at the end of the choice list.
* [Keyboard-en.plist.fix](https://github.com/witcher451/colemak-fix/blob/master/Keyboard-en.plist.fix)

## Mount Main Volume as Writeable
SIP doesn’t have to be disabled. After restart filesystem should be readable again, you may also try to mount it as readable from terminal in recovery mode.
sudo mount -uw /
sudo mount -ur /

## Disable / Enable System Integrity Protection
 [How to turn off rootless in Mac OS X El Capitan](http://www.macworld.co.uk/how-to/mac/how-turn-off-mac-os-x-system-integrity-protection-rootless-3638975/) 
1. Turn off your Mac (Apple > Shut Down).
2. Hold down Command-R and press the Power button. Keep holding Command-R until the Apple logo appears.
3. Wait for OS X to boot into the OS X Utilities window.
4. Choose Utilities > Terminal.
5. Enter **csrutil disable | enable**.
6. Enter reboot.

## Commands
Check SIP status 
`csrutil status`

Enable SIP
`csrutil enable`

Disable SIP
`csrutil disable`

 
#dev/config #dev/colemak
