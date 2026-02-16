# SynDrone-Swarm (Dataset)

SynDrone-Swarm is a telemetry-rich synthetic UAV swarm dataset designed to support benchmarking in:
(i) multi-drone detection, (ii) multi-object tracking, and (iii) short-horizon trajectory and intent prediction
under varying swarm density and domain shifts across two environments (**A/B**).

This repository is **data-only**: it provides documentation, manifests/schemas, and versioned download links.
The full dataset is distributed via **GitHub Releases**.

## Quick links
- Full dataset downloads: **Releases** → https://github.com/MehmetUnall/SynDrone-Swarm/releases
- Recommended citation: `CITATION.cff`

## Scenario matrix (v1.0.0)
All scenarios are recorded at **10 fps** for **120 s** per camera (**1,200 frames per camera**).
The dataset includes two domains (A and B), each with four scenarios: BAS, MED1, MED2, DEN.

| ID     | Env | Ego N_e | Adv N_a | Duration | Cameras | Frames (10 fps) | Total Frames |
|--------|-----|---------|---------|----------|---------|------------------|-------------|
| A-BAS  | A   | 5       | 1       | 120 s    | 5       | 1,200            | 6,000       |
| A-MED1 | A   | 8       | 1       | 120 s    | 8       | 1,200            | 9,600       |
| A-MED2 | A   | 8       | 2       | 120 s    | 8       | 1,200            | 9,600       |
| A-DEN  | A   | 12      | 3       | 120 s    | 12      | 1,200            | 14,400      |
| B-BAS  | B   | 5       | 1       | 120 s    | 5       | 1,200            | 6,000       |
| B-MED1 | B   | 8       | 1       | 120 s    | 8       | 1,200            | 9,600       |
| B-MED2 | B   | 8       | 2       | 120 s    | 8       | 1,200            | 9,600       |
| B-DEN  | B   | 12      | 3       | 120 s    | 12      | 1,200            | 14,400      |

## Folder structure
The dataset is organised by domain (A/B) and scenario, with per-camera folders:

```text
SynDrone-Swarm/
  A/
    A-BAS/
      telemetry.csv
      cam-EGO01/
        images/   (*.jpg + per-frame *.json)
        labels/   (YOLO *.txt)
        meta/
      cam-EGO02/ ...
  B/
    B-BAS/ ...
```

### Notes
- `labels.cache` files may appear under camera folders; these are optional cache files produced by training pipelines.

## Data formats
- **Images:** `cam-EGOxx/images/*.jpg` (RGB frames at 10 fps)
- **Per-frame JSON:** `cam-EGOxx/images/*.json` (frame metadata)
- **Bounding boxes (YOLO):** `cam-EGOxx/labels/*.txt` (normalised coordinates)
- **Telemetry:** `telemetry.csv` at each scenario root (per-frame drone states, roles, intent fields, etc.)

## Downloading the full dataset (GitHub Releases)
The full dataset is distributed as split archives (**each < 2 GiB**) plus SHA256 checksums.

1) Download all parts `SynDrone-Swarm.7z.001`, `SynDrone-Swarm.7z.002`, ... and `SHA256SUMS.txt` from the latest Release.
2) Place all files in the **same folder**.

**Windows (recommended)**
- Open/extract `SynDrone-Swarm.7z.001` with **7-Zip** (it will automatically use the remaining parts).

**Linux**
```bash
sha256sum -c SHA256SUMS.txt
7z x SynDrone-Swarm.7z.001
```

## Licence
- Data is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** licence.

## Citation
A recommended dataset citation is provided in `CITATION.cff`.
