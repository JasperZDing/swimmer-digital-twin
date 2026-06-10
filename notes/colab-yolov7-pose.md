# Colab YOLOv7 Pose Detection — Usage Guide

## Setup
Open in Colab: https://colab.research.google.com
Then upload `notebooks/yolov7_pose_detection.ipynb` from this project.

## What It Does
1. Clones YOLOv7 repo + downloads pose model weights (~75MB)
2. Prompts you to upload a swimming video (MP4, MOV, etc.)
3. Extracts frames (1 frame per second to keep POC manageable)
4. Runs YOLOv7-w6-pose inference on every frame
5. Outputs `pose_results.json` with per-frame COCO17 keypoints + downloads it
6. Shows a quick matplotlib preview of skeleton overlay on first 4 frames

## COCO 17 Keypoints
```
0: nose        5: left_shoulder   10: left_wrist    15: left_ankle
1: left_eye    6: right_shoulder  11: left_hip      16: right_ankle
2: right_eye   7: left_elbow      12: right_hip
3: left_ear    8: right_elbow 13: left_knee
4: right_ear   9: right_wrist     14: right_knee
```

Each keypoint: `[x, y, confidence]`

## Output Format (pose_results.json)
```json
{
  "frame_file": "frame_000000.jpg",
  "frame_idx": 0,
  "num_detections": 2, // multiple people possible
  "keypoints": [
    [[x, y, conf], [x, y, conf], ...],  // person 1 (17 kps)
    [[x, y, conf], [x, y, conf], ...]   // person 2
  ]
}
```

## After Running
1. Save `pose_results.json` to `data/` in this project
2. Next step: build lap counting / stroke detection logic on top of the keypoint sequence

## Tips
- **Video length**: Keep it short for the POC — 30-60 seconds is plenty
- **Camera angle**: Side-view (pool wall camera) works best for pose estimation
- **Water splashes**: Splashes can confuse the model — underwater segments are harder
- **Frame rate**: 1 fps extraction is fine for stroke analysis; higher only if you need fine-grained timing