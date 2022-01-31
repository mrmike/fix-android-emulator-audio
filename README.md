# fix-android-emulator-audio

The goal of the script is to fix common Bluetooth issue when running Android Emulator on macOS. Script modifies emulator configs in batch, so you don't have to do it manually, one by one.

## Installation
There're a few options to get and run the script.
1. git clone
```
git clone git@github.com:mrmike/fix-android-emulator-audio.git
# and call ./fix-android-emulator-audio inside repo directory
```
2. Homebrew
```
brew tap mrmike/homebrew-fix-android-emulator-audio
brew install fix-android-emulator-audio
# and call fix-android-emulator-audio from any location 
```
3. curl - you can use curl to get and run the script
```
curl -s https://raw.githubusercontent.com/mrmike/fix-android-emulator-audio/main/fix-android-emulator-audio | bash /dev/stdin
```

## Usage
Before calling the script make sure that emulator is closed.
```bash
 fix-android-emulator-audio

# Sample output
🔊 Processing emulators from: /Users/<USERNAME>/.android/avd
🔊 Processing - Pixel_5_API_31.avd
✅ Done - Pixel_5_API_31.avd
🔊 Processing - 4.7_WXGA_API_27.avd
✅ Done - 4.7_WXGA_API_27.avd
```

By default script will look on emulators located at `~/.android/avd`. Script accepts argument with custom `avd` directory localization
```bash
fix-android-emulator-audio path/to/your/avd/directory
```

Optionally you can pass `--wipe` option to wipe emulator's data so you don't have to do it manually via Android Studio. Script removes following files and directories:
```
* snapshots/
* userdata.img
* userdata-qemu.img
```

When running emulator for the first time after applying the fix make sure that data is wiped and emulator is started with Cold Boot option.
<p align="center">
 <img width="449" alt="coldboot" src="https://user-images.githubusercontent.com/529635/146804992-07182ed9-b195-4b0a-90fe-6adc3c79f2ec.png">
</p>

## How does it works
Script modifiy emulator config and disable audio input and output by specyfing
```
hw.audioInput=no
hw.audioOutput=no
```

## Credits
* Credits goes to Matt McKenna ([himattm](https://twitter.com/himattm)) for publishing article [Android Emulators vs Bluetooth Headphones](https://blog.mmckenna.me/android-emulators-vs-bluetooth-headphones)

## Contributions and contact
All pull requests are welcomed. You can contact me on Twitter at [@moczul](https://twitter.com/moczul)
