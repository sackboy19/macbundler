Small helper program to bundle your macOS binaries into a .app or .bundle file.

# READ ME!!
This was mostly written for fun, it is pretty useless and just adds another step to your build process.
I reccommend you just make your own plist and then use this: https://gist.github.com/sackboy19/012a83d5aec55a7c00542c4a2cb3ca98
So you just have a single shell script building your program

# 

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
1. You can use the `-only-plist` flag to tell macbundler to only generate an Info.plist file.
Example:
```sh
./macbundler app -name "My app" -binary myapp -bundle-identifier com.example -only-plist
```
2. Make the changes you want to the Info.plist file that was generated for you.
3. Then you can use macbundler again with the `-use-plist` command and supply it the path to that Info.plist file.
Example:
```sh
./macbundler app -name "My app" -binary myapp -bundle-identifier com.example -use-plist Info.plist
```

# Code signing / setting rpaths / universal binaries
Maybe I will support this later, however it is outside of the scope of what this simple program is for.
