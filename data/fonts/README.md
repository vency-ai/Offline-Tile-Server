 # Download the glyph PBFs for Noto Sans Regular
 ## Download prebuilt glyphs (no generation needed)
``` 
cd data/fonts
wget https://github.com/protomaps/basemaps-assets/archive/refs/heads/master.zip
unzip master.zip
mv basemaps-assets-master/fonts/* .
rm -rf basemaps-assets-master master.zip
```
## This gives you folders like:
```
data/fonts/Noto Sans Regular/0-255.pbf
data/fonts/Noto Sans Regular/256-511.pbf
… etc …
```

## Alternative#1: You can use .ttf convertion
### Download the entire family from

👉 https://github.com/notofonts/notofonts
 (or relevant Noto repo) and extract the SemiBold font file. (cloning the repo and picking out NotoSans‑SemiBold.ttf).

### Once you have the .ttf

Use your existing font‑to‑glyph pipeline to make PBFs:

If you’re using fontmaker / glyphmaker / fontnik:
```bash
fontnik generate \
  --font-file "NotoSans-SemiBold.ttf" \
  --output "data/fonts/Noto Sans SemiBold/{range}.pbf" \
  --ranges 0-255 256-511 512-767 …etc

```
#### (Adjust ranges to match the ones you already generated for your other fonts.)


## Alternative#2: Download All .pbf File
### Download the entire pbf directly  from
👉  https://www.juramap.org/fonts/noto_sans_semibold/Noto%20Sans%20SemiBold/

🐚 Using wget
```sh
cd data/fonts
mkdir -p 'Noto Sans Semibold'
cd 'Noto Sans Semibold'

wget -r -np -nH \
 --cut-dirs=3 \
 -R "index.html*" \
 https://www.juramap.org/fonts/noto_sans_semibold/Noto%20Sans%20SemiBold/

```
### What this does:

- -r: recursive download
- -np: don’t go up to parent directories
- -nH --cut-dirs=3: save files without the full site structure
- -R "index.html*": don’t save the index pages

After this runs you’ll have a folder with all the .pbf files in it.

## Keep the Same Folder Structure
```bash 
data/fonts/Noto Sans Semibold/
    0-255.pbf
    256-511.pbf
    ...
```