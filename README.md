# youtube_to_txt

Download audio from a YouTube video and transcribe it to a timestamped text file using [yt-dlp](https://github.com/yt-dlp/yt-dlp) and [faster-whisper](https://github.com/SYSTRAN/faster-whisper).

## Requirements

- Python 3.10+
- [FFmpeg](https://ffmpeg.org/) (used by yt-dlp to convert audio to MP3)

Install FFmpeg on macOS with Homebrew:

```bash
brew install ffmpeg
```

## Setup

1. Clone this repository and open `code.ipynb` in Jupyter or VS Code / Cursor.
2. Select a Python kernel (use the same environment for install and run).
3. In the first notebook cell, install dependencies into the **active kernel**:

```python
%pip install yt-dlp faster-whisper
```

Use `%pip`, not `!pip`, so packages install into the kernel that runs your code.

## Usage

Run the cells in `code.ipynb`, or use the functions directly:

1. Paste a YouTube URL when prompted.
2. Audio is saved under `downloads/` as MP3.
3. A transcript is written to `downloads/{video title}_transcript.txt` with timestamps per segment.

Example output line:

```
[12.50 - 18.30] Hello and welcome to the stream.
```

## Project layout

```
youtube_to_txt/
├── code.ipynb      # Main notebook
├── downloads/      # Downloaded audio (gitignored)
└── README.md
```

## Notes

- The first run downloads the Whisper `base` model; later runs reuse the cached model.
- Transcription uses CPU with `int8` compute type by default. For GPU support, change `device` and `compute_type` in `transcribe_audio`.
- yt-dlp may warn about a JavaScript runtime for some YouTube formats. Downloads usually still work; see the [yt-dlp EJS wiki](https://github.com/yt-dlp/yt-dlp/wiki/EJS) if you hit extraction errors.

## License

Use and modify as you like. Respect YouTube’s terms of service and copyright when downloading and transcribing content.
