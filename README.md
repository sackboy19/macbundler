Small helper program to bundle your macOS binaries into a .app or .bundle file.

Usage:
```sh
./macbundler
  <app or bundle> \
  -name "My App" \
  -binary yourbinary \
  -bundle-identifier com.example.blah \
  -o <output-directory> \ # optional
  -assets <folder-with-resources> \ # optional
  -icon myicon.icns \ # optional
  -frameworks <folder-with-libs-or-frameworks> \ # optional
  -only-plist \ # optional
  -use-plist myinfo.plist \ # optional
```

# Example usage:
```sh
./macbundler app -name "Cool app" -binary cool_app -bundle-identifier com.danny.coolapp -o . -assets MyResourcesFolder -icon myicon.icns -frameworks MyLibs

# or for a .bundle
./macbundler bundle -name "Cool bundle" -binary cool_bundle -bundle-identifier com.danny.coolbundle -o . -assets MyResourcesFolder -icon myicon.icns -frameworks MyLibs
```

# How to customize Info.plist?
Why? Because there is a lot of different keys you can put in the Info.plist, and I'm not going to support all of them.
For example a useful key is the CFBundleSupportedPlatforms key. With that you can specify what platforms your App runs on.

1. You can use the `-only-plist` flag to tell macbundler to only generate an Info.plist file.
Example:
```sh
./macbundler app -name "My app" -binary myapp -bundle-identifier com.example -only-plist
```
3. Make the changes you want to the Info.plist file that was generated for you.
4. Then you can use macbundler again with the `-use-plist` command and supply it the path to that Info.plist file.
Example:
```sh
./macbundler app -name "My app" -binary myapp -bundle-identifier com.example -use-plist Info.plist
```

# Code signing / settings rpaths / universal binaries
Maybe I will support this later, however it is outside of the scope of what this simple program is for.
This program is mainly just a small tool to help me generate a .app file for my current project I'm working on.
I don't want to put too much work into this tool because Platin21 is working on adding a macOS bundler to the Odin compiler itself, which would fully handle all those features and more.
