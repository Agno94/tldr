# ffprobe

> Extracts tracks from Matroska files.
> More information: <https://mkvtoolnix.download/doc/mkvextract.html>.

- Extrack the first track from a `mkX` media file:

`mkvextrack {{movie.mkv}} tracks 0:video.h265`

- Extract metadata and chapters information as xml files:

`mkvextract {{movie.mkv}} chapters {{movie_chapters.xml}} tags {{movie_tags.xml}}`

- Extrack the first 4 tracks from a media file:

`mkvextrack {{movie.mkv}} tracks 0:{{video.vp9}} 1:{{audio_track_1.opus}} 2:{{audio_track_2.ogg}} 3:{{subtitle.srt}}`

- Extract the last video track

``mkvextract {{movie.mkv}} tracks `mkvinfo --ui-language en_US {{movie.mkv}} | grep -B 100 "Track type: video" | grep "Track number" | tail -n 1 | sed "s|^.*mkvextract: \([0-9]*\).*$|\1|"`:{{video.ext}}``

- Save an attachment located in the `4`-th track of a media file

`mkvextract {{song.mka}} attachments {{4}}:{{album_cover.jpg}}`
