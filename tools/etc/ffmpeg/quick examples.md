- convert .mov to .gif

```sh
ffmpeg -i input.mov -vf "fps=10,scale=480:-1:flags=lanczos" -c:v gif output.gif
```

- compress video

```sh
ffmpeg -i input.mp4 -vcodec libx264 -crf 28 -preset slow -acodec aac -b:a 128k output.mp4
```

   - crf can be set to higher value for higher compression