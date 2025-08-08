# Mapping reads against a reference

In order to map your filtered reads against a reference you will need to use the [BBMap](https://sourceforge.net/projects/bbmap/) package.

You do not need an environment to run BBMap since it "is written in pure Java, can run on any platform, and has no dependencies other than Java being installed".

Thus, just download the package and extract it to `/mnt/c/MARRIO_genomics/`:

```
wget https://sourceforge.net/projects/bbmap/files/BBMap_39.33.tar.gz -P /mnt/c/MARRIO_genomics/
tar -xvzf /mnt/c/MARRIO_genomics/BBMap_39.33.tar.gz -C /mnt/c/MARRIO_genomics/
rm /mnt/c/MARRIO_genomics/BBMap_39.33.tar.gz
```

