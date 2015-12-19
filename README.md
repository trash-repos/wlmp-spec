# wlmp-spec
WLMP (Windows Live MovieMaker Project) Unofficial Specification

**NOTE: Work in progress!**

## General
A `wlmp` file is an xml document with the basic structure looking approx. like this:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project name="My Project" themeId="0" version="65540" templateID="SimpleProjectTemplate">
  <MediaItems/>
  <Extents />
  <BoundPlaceholders />
  <BoundProperties />
  <ThemeOperationLog themeID="0">
    <MonolithicThemeOperations />
  </ThemeOperationLog>
  <AudioDuckingProperties emphasisPlaceholderID="Narration" />
</Project>
```

## <Project>
 * children:
   * `<MediaItems>`
   * `<Extents>`
   * `<BoundPlaceholders>`
   * `<BoundProperties>`
   * `<ThemeOperationLog>`
   * `<AudioDuckingProperties>`
 * attributes:
   * `name`
   * `themeId` – defaults to `"0"`
   * `version` – version of MovieMaker? TODO investigate
   * `templateID` – defaults to `SimpleProjectTemplate`

## <AudioDuckingProperties>
 * children: none
 * attributes:
   * `emphasisPlaceholderID`
     * `""` – balanced
     * `"SoundTrack"` – emphasize music
     * `"Narration"` (default) – emphasize narration
     * `"Main"` – emphasize sound of video

## <MediaItems>
 * children: `<MediaItem>`

# <MediaItem>
 * children: none
 * attributes:
   * `id` – integer, autoincrement, begins with `"1"`
   * `filePath` – absolute path to the file
   * `mediaItemType`
     * `"1"` – it's a video file
     * `"2"` – it's an image
     * `"3"` – it's an audio file
   * `arWidth`
     * if `mediaItemType="1"` – the width in pixels
     * if `mediaItemType="2"` – some strange value – for 4608x3072 it's `"96"`
     * if `mediaItemType="3"` – always `"0"`
   * `arHeight`
     * if `mediaItemType="1"` – the height in pixels
     * if `mediaItemType="2"` – some strange value – for 4608x3072 it's `"64"`
     * if `mediaItemType="3"` – always `"0"`
   * `duration`
   * `songTitle`
   * `songArtist`
   * `songAlbum`
   * `songCopyrightUrl`
   * `songArtistUrl`
   * `songAudioFileUrl`
   * `stabilizationMode`
