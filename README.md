## ISD‑FINE: the Dual Inter-layer Self-Distillation for Fine-Grained Distribution Refinement and Attention Weight Calibration in DETRs

**ISD‑FINE** is an enhanced version of the [D‑FINE: Redefine Regression Task of DETRs as Fine‑grained Distribution Refinement]  
(https://github.com/your-org/D-FINE) model, modified to improve decoder performance.

### Model Overview  
- **Base Project:** D‑FINE (2024) © The D‑FINE Authors. All Rights Reserved.  
- **Secondary Source:** Originally forked from RT‑DETR (2023) © lyuwenyu. All Rights Reserved.  

### Acknowledgements  
We gratefully acknowledge the original D‑FINE authors for their foundational work and lyuwenyu for RT‑DETR, on which this implementation builds. Including an “Acknowledgements” section in your README is a widely recommended practice to give proper credit to upstream projects and contributors :contentReference[oaicite:0]{index=0}.

### Key Modifications  
All changes live in the decoder component—specifically, in `src/zoo/dfine/dfine_decoder.py`.  

1. **Inter‑layer Self‑Distillation**  
   - Replaced the original GO‑LSD (Global‑Local Semantic Distillation) scheme with an **inter‑layer self‑distillation** framework.  
   - Each decoder layer now distills knowledge into the next layer, improving feature propagation and stabilizing training :contentReference[oaicite:12]{index=12}:contentReference[oaicite:13]{index=13}:contentReference[oaicite:14]{index=14}:contentReference[oaicite:15]{index=15}:contentReference[oaicite:16]{index=16}:contentReference[oaicite:17]{index=17} :contentReference[oaicite:18]{index=18}:contentReference[oaicite:19]{index=19}:contentReference[oaicite:20]{index=20}:contentReference[oaicite:21]{index=21}:contentReference[oaicite:22]{index=22}:contentReference[oaicite:23]{index=23}.  

2. **Self‑Distillation in Attention Weights**  
   - Introduced self‑distillation directly on the decoder’s multi‑head attention weights: each head’s attention map from layer *L* is used as a “soft target” for the same head in layer *L+1*.  
   - This encourages consistency across layers and sharpens object localization cues :contentReference[oaicite:24]{index=24}:contentReference[oaicite:25]{index=25}:contentReference[oaicite:26]{index=26}:contentReference[oaicite:27]{index=27}:contentReference[oaicite:28]{index=28}:contentReference[oaicite:29]{index=29} :contentReference[oaicite:30]{index=30}:contentReference[oaicite:31]{index=31}:contentReference[oaicite:32]{index=32}:contentReference[oaicite:33]{index=33}:contentReference[oaicite:34]{index=34}:contentReference[oaicite:35]{index=35}.  


### License and SPDX  
This project is released under the Apache‑2.0 License. See [`LICENSES/Apache-2.0.txt`](LICENSES/Apache-2.0.txt).  
For machine‑readable licensing, we include an SPDX identifier in each source file and summarize it here in the README :contentReference[oaicite:2]{index=2}.

### File Structure  
```
├── src/
│   └── zoo/
│       └── dfine/
│           └── dfine_decoder.py    ← Main modifications here
└── README.md
