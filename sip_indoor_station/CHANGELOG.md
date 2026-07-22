## 0.2.0-opus.1

- **Configurable audio codec** via `audio_codec_preference` (default `PCMA,PCMU`
  → identical to upstream). Set to `OPUS,PCMA` to negotiate wideband Opus with
  door stations that offer it.
- Core installed from fork branch `feat/configurable-audio-codec-opus`.
- Opt-in and backward compatible.
