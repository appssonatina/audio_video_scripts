
# Simple ffmpeg command invocation

```ffmpeg -y -i video.avi -s vga video.mp4```

> **-y** 
>> Overwrite existing file
>
> **-s framesize** 
>> (vga -> 640x480)

# Generate rgb colors and output to SDL window

```ffmpeg -f lavfi -i rgbtestsrc -pix_fmt yuv420p -f sdl Example```


> **-f lavfi** 
>> Format lavfi
>
> **-i rgbtestsrc** 
>> Input command received by lavfi
>
> **-pix_fmt yuv420p** 
>> Pixel format to yuv420p
>
> **-f sdl Example** 
>> Output format and name


# Specify bitrate which affects quality

```ffmpeg -y -i example.mp4 -b:v 12K output.mp4```

> **-b:v 12K** 
>> Bitrate for video

# Another example to reencode the video with smaller size

```ffmpeg -i output.mkv -c:v libx264rgb -crf 0 -preset veryslow output-smaller.mkv```

# List formats available for webcam (Video4Linux2)

```ffmpeg -f v4l2 -list_formats all -i /dev/video0```

# Filters are applied between input and output

```ffplay -f lavfi -i testsrc -vf transpose=1```

> **-vf transpose=1** 
>> Is video filter to rotate the video


# Simple example of audiofilter

```ffplay -f pulse -i default -af atempo=0.8```

> **-f pulse** 
>> Specify the format. "pulse" allows to grab audio from mic
>
> **-i default** 
>> Use the default Pulseaudio input device
>
> **-af atempo=0.8**
>> Apply audio filter


# To record the desktop

```ffmpeg -video_size 1024x768 -framerate 25 -f x11grab -i :0.0+100,200 -f pulse -ac 2 -i default -c:v libx264rgb -crf 24 -preset ultrafast output.mkv```

> **-i display**
>> -i track the display (:0.0) and the top left corner (+100,200)
>
> **-framerate** 
> **-crf** 
> **-preset** 
>> options will influence the quality vs size
> 
> **-preset val** 
>> can take the values: ultrafast, fast, medium, slow and veryslow


# Example to record audio from mic with still picture and save as video file

```ffmpeg -loop -1 -i image.jpg -f pulse -ac 2 -i default -c:v libx264rgb -crf 24 -preset veryslow output.mkv```

> **-loop** 
>> is used to show the image since the beginning of the video


