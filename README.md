Small helper program to bundle your macOS binaries into a .app or .bundle file.

Usage:
```sh
./macbundler
  <app or bundle> \
  -name "My App" \
  -binary yourbinary \
  -bundle-identifier com.example.blah \
  -o <output-directory> \ # optional
  -assets ./folder_with_resources \ # optional
  -icon appicon.icns \ # optional
  -frameworks <folder_with_libs_or_frameworks> \ # optional
```

Example usage:
```sh
./macbundler app -name "Cool app" -binary cool_app -bundle-identifier com.danny.coolapp -o . -assets MyResourcesFolder -icon myicon.icns -frameworks MyLibs

# or for a .bundle
./macbundler bundle -name "Cool bundle" -binary cool_bundle -bundle-identifier com.danny.coolbundle -o . -assets MyResourcesFolder -icon myicon.icns -frameworks MyLibs
```
