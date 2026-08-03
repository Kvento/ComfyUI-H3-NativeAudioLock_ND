# MiniMax H3 Native-Audio Music Video Workflow

This package provides two ComfyUI templates used for the local MiniMax H3 music-video workflow.

## Included

- `custom_nodes/ComfyUI-H3-NativeAudioLock/`: locks the supplied source audio into the H3 audio latent and returns that exact audio for the saved video.
- `workflows/MiniMaxH3_NativeAudio_MusicVideo_TEMPLATE.json`: a blank, annotated H3 music-video starting point.
- `workflows/RIFE_WAN_Method_Interpolation_TEMPLATE.json`: the standalone RIFE interpolation branch based on the supplied WAN 2.2 loop workflow.

## Install

1. Copy `custom_nodes/ComfyUI-H3-NativeAudioLock` to `ComfyUI/custom_nodes/`.
2. Copy both JSON files to `ComfyUI/user/default/workflows/`.
3. Restart ComfyUI. The interpolation template additionally needs `ComfyUI-Frame-Interpolation` and its RIFE model (`rife47.pth`).

## Music-video prompt template

Use one character reference for each new scene. Continue a scene from the actual final frame of the previous clip.

```
Use <Picture 1> as the exact character identity and scene anchor: [identity, outfit, setting].
[What the character does] with [camera movement].
[Lip-sync instruction: "sing the exact supplied vocal audio with natural, precise lip synchronization" OR "lips remain fully closed for every frame"].
Maintain [locked palette / lighting / time of day / background details].
No [unwanted changes: sun, daylight, warm orange/gold grade, text, logo, extra people, environmental morphing].
```

Audio timing matters: trim the source song to the exact start and duration of each clip. Use the native-audio lock node immediately after the H3 video-conditioning node. At non-vocal timestamps, explicitly instruct the model that the mouth remains closed.

## Interpolation guidance

The RIFE branch is preferable to basic CPU optical-flow interpolation for generated footage. For a 24 fps source, generate 5× intermediate timing (120 fps), then decimate to a 60 fps deliverable while keeping the original audio. Upscale after interpolation; use a dedicated RTX/TensorRT or modern AI upscaler on the final 60 fps stream.
