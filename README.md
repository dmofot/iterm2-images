# iterm2-images
Inline image scripts for iTerm2

This repository contains the scripts needed to do inline images [1] in iTerm2, making `$ brew install` possible.  They are pulled directly and without any changes from [George Nachman](https://github.com/gnachman)'s [iTerm2-website](https://github.com/gnachman/iterm2-website) repository, specifically from [utilities](https://github.com/gnachman/iterm2-website/tree/master/source/utilities).  

See the [homebrew tap repo](https://github.com/dmofot/homebrew-tap) for installation using [homebrew](https://brew.sh/).  

You can check the sha256 between the local and [iTerm2-website](https://github.com/gnachman/iterm2-website) files using something like:  
```bash
# Remote URIs
iterm2_imgls='https://raw.githubusercontent.com/gnachman/iterm2-website/master/source/utilities/imgls'
iterm2_imgcat='https://raw.githubusercontent.com/gnachman/iterm2-website/master/source/utilities/imgcat'

# File locations of local image scripts
local_imgls='https://raw.githubusercontent.com/dmofot/iterm2-images/master/imgls'
local_imgcat='https://raw.githubusercontent.com/dmofot/iterm2-images/master/imgcat'

# Determine sha256 checksums of online iTerm2 image scripts
iterm2_imgls_sha256="$(curl -sL "$iterm2_imgls" | shasum -a 256 | cut -d ' ' -f 1)"
iterm2_imgcat_sha256="$(curl -sL "$iterm2_imgcat" | shasum -a 256 | cut -d ' ' -f 1)"

# Determine sha256 checksums of local image scripts
local_imgls_sha256="$(curl -sL "$local_imgls" | shasum -a 256 | cut -d ' ' -f 1)"
local_imgcat_sha256="$(curl -sL "$local_imgcat" | shasum -a 256 | cut -d ' ' -f 1)"

# Check if sha256 checksums are different between remote iTerm2 image scripts and local
if [ "$iterm2_imgls_sha256" != "$local_imgls_sha256" ]; then
    echo "Warning: iTerm2 imgls sha256 checksum is different than local"
else
    echo "Remote and local imgls sha256 checksum is the same"
fi

if [ "$iterm2_imgcat_sha256" != "$local_imgcat_sha256" ]; then
    echo "Warning: iTerm2 imgcat sha256 checksum is different than local"
else
    echo "Remote and local imgcat sha256 checksum is the same"
fi
```

[1]: [iTerm2 Image Documentation](https://www.iterm2.com/documentation-images.html)