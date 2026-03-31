# Audora Media

Media files (songs and cover art) for the [Audora](https://github.com/priyanshuwq/audora) music streaming app.

## Structure

```
audora-media/
├── songs/                    # Audio files (.mp3)
└── extracted-covers/         # Album cover art (.jpg, .jpeg)
```

## Usage

This repository is served via GitHub Pages as a static CDN for the main Audora application.

**Production URL:** `https://priyanshuwq.github.io/audora-media/`

### Configuration

Set the following environment variable in your Audora deployment:

```bash
VITE_MEDIA_BASE_URL=https://priyanshuwq.github.io/audora-media
```

## File Counts

- 620 songs (.mp3)
- ~525 gitcover images (.jpg, .jpeg)

## Chunked Push For Large Songs Folder

Use the helper script to commit and push `songs/` in smaller size-based chunks.

```bash
# Preview chunks without changing git history
bash scripts/push-songs-in-chunks.sh --dry-run --chunk-mb 300

# Commit and push songs in ~300MB chunks
bash scripts/push-songs-in-chunks.sh --chunk-mb 300

# Resume from a failed chunk (example: start from chunk 4)
bash scripts/push-songs-in-chunks.sh --chunk-mb 300 --start-chunk 4
```

### Notes

- The script only processes modified/untracked files under `songs/`.
- It creates one commit per chunk and pushes after each commit.
- It checks for GitHub's 100MB per-file hard limit before running.

## License

Media files are for personal use only.
