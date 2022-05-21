`HTTP Live Streaming (HLS)` - A media streaming communications protocol. It breaks the overall stream into a sequence of small file downloads.

As the stream is played, the client may select from a no. of different alternate streams containing the same material encoded at a variety of different data rates. At the start of the streaming session, an extended M3Y (m3u8) playlist containing the meta data of various available sub-streams is downloaded.

`m3u` is a file format that stores multimedia playlists. It is basically a plain text file that specifies the location of one or more media files.

`m3u` files normally use Latin-1 character set. The unicode version of m3u is m3u8, which uses UTF-8 unicode characters.

HTTP Live Streaming supports both live broadcasts and prerecorded content (video on demand).
