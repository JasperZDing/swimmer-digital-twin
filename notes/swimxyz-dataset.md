# SwimXYZ Dataset — Downloaded & Available Data

## Source
https://g-fiche.github.io/research-pages/swimxyz/
ACM MIG 2023 — Fiche et al.

## Downloaded (in `data/`)
| File | Size | Description |
|------|------|-------------|
| `swimxyz_sample.mp4` | 9.3 MB | Sample swimming video (teaser, synthetic) |
| `smpl_swimming_motions.zip` | 55.2 MB | Ground truth SMPL skeletal motions (240 sequences) |

## Available on Zenodo (NOT YET downloaded)
### Annotations + SMPL motions
- `smpl_swimming_motions.zip` ✅ downloaded
- `Backstroke_labels.zip` — 1.5 GB (ground truth 2D/3D joints)
- `Freestyle_labels.zip` — 1.6 GB
- `Butterfly_labels.zip` — 1.6 GB
- `Breaststroke_labels.zip` — 1.6 GB

### Videos (300 GB total — too large for POC download)
| Stroke | Part | Size |
|--------|------|------|
| Backstroke | part1 | 36.5 GB |
| Backstroke | part2 | 32.8 GB |
| Breaststroke | part1 | 36.6 GB |
| Breaststroke | part2 | 31.1 GB |
| Butterfly | part1 | 36.9 GB |
| Butterfly | part2 | 31.6 GB |
| Freestyle | part1 | 37.5 GB |
| Freestyle | part2 | 33.6 GB |

## What to Use for POC
- **Sample video** (`swimxyz_sample.mp4`) → test YOLOv7 pose detection in Colab
- **SMPL motions** (`smpl_swimming_motions.zip`) → validate stroke motion patterns (SMPL → COCO keypoint conversion possible)
- **Full videos** → only if doing large-scale training; not needed for POC

## Next Steps
1. Upload `swimxyz_sample.mp4` to Colab and run YOLOv7 pose detection notebook
2. Extract and inspect SMPL motions content (zip contains `.npz` or similar SMPL param files)
3. Optionally: pick one small Zenodo video archive if we need real video data