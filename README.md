# media scripts
scripts to do media conversion stuff, mostly with ffmpeg

## empty audio
Sometimes you want an empty audio file, for example if you listen to music before going to bed.

The ones online, [like in this repo](https://github.com/anars/blank-audio) are pretty big. The bottlenecks are always the minimum quality settings that codecs support, as they really didn't intend to be used for this purpose.

So I found the smallest possible audio format!
- `AAC` codec
- 4000Hz "input" samplerate
- 1kHz bitrate
- mono channel

A 24h long silent audio is under 5MB, which is not great, but better than everything else!

I tested opus, wav, raw and mp3. All either have higher minimum quality settings, or don't compress as well.

If you find a way to make them even smaller, please share!

## `flac` and `wav` to `ogg opus`
`opus` is the successor to `vorbis` and a really great, lossy codec that (for me) preserves audible audio 100%.

You can test how much `opus` takes from your beloved `flac` files, by doing this:
1. Get [Audacity](https://flathub.org/apps/org.audacityteam.Audacity) or [Tenacity](https://flathub.org/apps/org.tenacityaudio.Tenacity)
2. Configure that outdated garbage app to read your files
3. Compress a `flac` or `wav` file with ogg opus
4. Load the lossy file into audacity, load the lossless file as seconds track
5. Select the track with the compressed file, go to "Effects" "Special" and "Invert"
6. Press the "Play" button

You will only hear what is left in the lossless file, but not in the lossy one. While AAC and mp3 remove noticeable things, I wasn't able to hear anything with opus.

## `mpd` to `opus`, `exo` to `m4a`
These seem to be strange file formats that actually contain opus and AAC audio.

The conversion is quick and makes them playable with many players.
