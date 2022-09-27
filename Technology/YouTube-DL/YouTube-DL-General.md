# YouTube-DL

## Overview
Download videos from [YouTube](https://www.youtube.com/) or other video
platforms.

## Configuration

Configuration: `youtube-dl.conf`
Location:

```plaintext
# Lines starting with # are comments

# Download best video format and best audio format without merging them
#-f 'bestvideo,bestaudio'
# Download best audio format
-f "bestaudio[ext=flac]/best"

# Always extract audio
-x

# Extract FLAC audio
--audio-format "flac"

# Verbose
-v
```

## Reference

### General
* [youtube-dl](https://youtube-dl.org/){:target="_blank"}
* [youtube-dl (GitHub)](https://github.com/ytdl-org/youtube-dl/){:target="_blank"}