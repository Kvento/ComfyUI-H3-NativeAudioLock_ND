### This fork based on [MiniMax-H3-NativeAudio-MusicVideo-Workflow](https://github.com/Shrek3OnVH5/MiniMax-H3-NativeAudio-MusicVideo-Workflow)


# MiniMax H3 Native Exact-Audio Lock

This package provides MiniMax H3 Native Exact-Audio Lock ComfyUI node and template used for the local MiniMax H3 music-video workflow.

## Included

- `MiniMax H3 Native Exact-Audio Lock`: locks the supplied source audio into the H3 audio latent and returns that exact audio for the saved video.
- `workflows/MiniMaxH3_NativeAudio_MusicVideo_TEMPLATE.json`: a blank, annotated H3 music-video starting point.


## Install

1. Open a terminal in ComfyUI/custom_nodes and run: 
```bash
git clone https://github.com/Kvento/ComfyUI-H3-NativeAudioLock_ND
```
2. Restart ComfyUI.


## Music-video prompt template

```
Use <Picture 1> as the exact character identity and scene anchor: [identity, outfit, setting].
[What the character does] with [camera movement].
[Lip-sync instruction: "sing the exact supplied vocal audio with natural, precise lip synchronization" OR "lips remain fully closed for every frame"].
Maintain [locked palette / lighting / time of day / background details].
No [unwanted changes: sun, daylight, warm orange/gold grade, text, logo, extra people, environmental morphing].
```

Audio timing matters: trim the source song to the exact start and duration of each clip. Use the native-audio lock node immediately after the H3 video-conditioning node. At non-vocal timestamps, explicitly instruct the model that the mouth remains closed.

## Creditts
- [Shrek3OnVH5](https://github.com/Shrek3OnVH5)
