# Unicode distro logos

This repository includes the logos of various Linux distributions in the form of unicode text art. The logos are meant to be displayed in a terminal emulator. Your terminal program needs to support 256 colors, also the display quality of the logos is strongly affected by the exact font you use. 

The logo files can be found in the `textlogos` directory under subdirectories named after the respective Linux distro. For most distros there are two base versions: one with a framed background, and one with simple black background. For a few distros there are also alternative versions too.

In each directory you'll find three kind of logos:
* **_32x32.txt** - 32x32 resolution pixelated version, using unicode block characters
* **_72x72.txt** - 72x72 resolution pixelated version, using block characters from the Unscii font
* **_high.txt** - more detailed 72x72 pixel version, which uses various other characters from the Unscii font

The `_32x32` version uses common unicode block characters. Most fonts do include these characters. However when displayed, most of the time they are not placed correctly in relation to each other. Thus the logo art will be messed up to some extent, that varies by specific fonts.

These versions were generated by using `gotermimg`, which was created by Colin Kennedy, you can find more info about it at the following repo: https://github.com/moshen/gotermimg

The `_72x72` and `_high` versions are meant to be displayed with the Unscii font created by Viznut. It's not that you won't see anything with other fonts, just that the exact characters that were used are only included in this one font. You can download it on the following site: http://pelulamu.net/unscii/

For converting the logos to the right format I used a binary named `bm2uns`. You can find this file in the source code download of Unscii too.

## Usage
You can simply `cat` the logo files in your terminal. Additionaly you can use them with various system info programs, that displays a logo. 

### Usage with alsi
```
alsi -f path/to/logo_file_of_your_choice
```
### Usage with screenfetch
You'll need to make a script file with the following content. Change the path to the logo file of your choice
```
startline=1
readarray -t fulloutput <<< "`sed -e '2,$s/$/%s/' textlogos/archlinux/archlinux_72x72.txt`"
```
and then feed it to screenfetch this way:
```
screenfetch -a path/to/the_script_file_you_created
```

## Misc

This repo also includes the source image files, and also the Gimp `xcf` files, that the logo images were exported from. Of course the original logos of the various distros were not created by me.

I also included a script file named `generate.sh`. This can generate all the logo text files at once (if a folder is given as parameter) or just the variants for one given image (if the parameter is an image file)
