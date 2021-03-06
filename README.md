# numbright

Repository for controlling screen brightness on an Asus Zenbook running Ubuntu. This project was inspired by a post I saw on stackoverflow and then customized to my liking.  

## File Setup
    1) Put setbright, numbright, incrbright, & decrbright in ~/bin  
    2) Make sure $HOME/bin is in the PATH variable  
	check this by looking at the path setting in your bash login file  
    3) Make setbright, numbright, incrbright, & decrbright executable  
         if you don't know how, google, "sudo chmod +x"  
    4) Open /etc/default/grub as a superuser  
         change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
         to     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="  
         save and close the file  
         this will activate the fn+F5 and fn+F6 key combinations  
    5) Run 'sudo update-grub' in a terminal
    6) Install xbacklight with apt
    7) Restart  
    8) Check which directories exist in /sys/class/backlight  
         The script numbright is designed to change /sys/class/backlight/acpi_video0/brightness because that brightness file uses the integers 1-10, which makes setting the brightness step size much easier.   
         Depending on your file system configuration, you may need to change the directory hierarchy.  
         A common directory is /sys/class/backligt/intel_backlight/ The setbright script is an older script that interfaces with it.  
         To use setbright instead of numbright, update incrbright and decrbright to interface with setbright and pass the appropriate parameters (refer to the comments in setbright to do that)  
    
    
## Setup
 * Bind incrbright to the key combination you want to brighten your screen  
 * Bind decrbright to the key combination you want to dim your screen  
 * Restart  
 *   The keys should now adjust brightness  

## Usage Examples

```
numbright 3      - sets acpi_video0/brightness to 3 (integer values [1, 10])
numbright +1     - increases acpi_video0/brightness value by 1
numbright -1     - decreases acpi_video0/brightness value by 1

setbright 42     - sets screen brightness to 42% of maximum brightness
setbright +10    - increases screen brightness by 10 percentage points
setbright -15    - decreases screen brightness by 15 percentage points
```

## Author

Marion Anderson - [lowdrant](https://github.com/lowdrant)

## Acknowledgements/References
 * https://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script
  * https://askubuntu.com/questions/471847/brightness-fn-key-shortcut-doesnt-work-on-asus-laptop
 * https://stackoverflow.com/questions/2304863/how-to-write-a-good-readme
 * https://robots.thoughtbot.com/how-to-write-a-great-readme
