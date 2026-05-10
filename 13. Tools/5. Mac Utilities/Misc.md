##### Downloading audio from YouTube/Instagram videos

It can be done using the Homebrew package **yt-dlp**. The file gets saved in the current working directory. **ffmpeg** is another dependency that you'd have to install manually.

```
brew install ffmpeg
brew install yt-dlp
yt-dlp -x --audio-format mp3 <VIDEO_URL>
```

[ChatGPT link](https://chatgpt.com/c/69bac86a-510c-8328-8633-07b7e812a685)

To download multiple videos together (save the URLs in a txt file) -

```
cat urls.txt | xargs -n 1 -P 4 yt-dlp -x --audio-format mp3
```



##### Creating a video from a still image (png) and audio (mp3)

```
ffmpeg -loop 1 -i <imageFile>.jpg -i <audioFile>.mp3 -c:v libx264 -tune stillimage -c:a aac -b:a 192k -shortest -pix_fmt yuv420p output.mp4
```

https://www.instagram.com/reels/DH0zQq-zn2g/



yt-dlp -x https://www.instagram.com/reels/DH0zQq-zn2g/
