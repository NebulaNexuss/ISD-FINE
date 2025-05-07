## ISD‑FINE: the Dual Inter-layer Self-Distillation for Fine-Grained Distribution Refinement and Attention Weight Calibration in DETRs

**ISD‑FINE** is an enhanced version of the [D‑FINE: Redefine Regression Task of DETRs as Fine‑grained Distribution Refinement]  
(https://github.com/your-org/D-FINE) model, modified to improve decoder performance.

### Model Overview  
- **Base Project:** D‑FINE (2024) © The D‑FINE Authors. All Rights Reserved.  
- **Secondary Source:** Originally forked from RT‑DETR (2023) © lyuwenyu. All Rights Reserved.  

### Acknowledgements  
We gratefully acknowledge the original D‑FINE authors for their foundational work and lyuwenyu for RT‑DETR, on which this implementation builds. 

### Key Modifications  
All changes live in the decoder component—specifically, in `src/zoo/dfine/dfine_decoder.py`.  

1. **Inter‑layer Self‑Distillation**  
   - Replaced the original GO‑LSD (Global‑Local Semantic Distillation) scheme with an **inter‑layer self‑distillation** framework.  
   - Each decoder layer now distills knowledge into the adjacent shallower layer, improving feature propagation and stabilizing training.  

2. **Self‑Distillation in Attention Weights**  
   - Introduced self‑distillation directly on the decoder’s multi‑head attention weights: each head’s attention map from layer *L+1* is used as a “soft target” for the same head in layer *L*.  
   - This encourages consistency across layers and sharpens object localization cues.  


### License and SPDX  
This project is released under the Apache‑2.0 License. See [`LICENSES/Apache-2.0.txt`](LICENSES/Apache-2.0.txt).  
For machine‑readable licensing, we include an SPDX identifier in each source file .

### File Structure  
```
├── src/
│   └── zoo/
│       └── dfine/
│           └── dfine_decoder.py    ← Main modifications here
└── README.md
