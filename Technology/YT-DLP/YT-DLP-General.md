# YT-DLP

## Table of Content
* [Overview](#overview)
* [Reference](#reference)
    * [General](#general)

## Overview

YT-DLP is a feature-rich command-line audio/video downloader with
support for [thousands of sites](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md).
The project is a fork of [youtube-dl](https://github.com/ytdl-org/youtube-dl)
based on the now inactive [youtube-dlc](https://github.com/blackjack4494/yt-dlc).

## Usage

### Common

List available formats of each video.

```bash
yt-dlp --list-formats "<URL>"
```

Multiple filter

```bash
yt-dlp --format "bv*[ext=webm]+ba[ext=webm][acodec=opus]" "<URL>"
```

## Reference

### General

* [yt-dlp (GitHub)](https://github.com/yt-dlp/yt-dlp)

### Miscellaneous

* [How to Use the Command `yt-dlp` (with Examples)](https://commandmasters.com/commands/yt-dlp-common/)
* [V1 vs VP9: Which codec should you choose?](https://imagekit.io/blog/av1-vs-vp9/)
