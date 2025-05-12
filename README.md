# Decoding Visual Similarities of Stimuli through Neural Responses

This project investigates whether **visual stimuli that evoke similar neural responses in the mouse brain also share similar visual characteristics**. We use real data from the Allen Brain Observatory to analyze spiking activity in the visual cortex of mice while exposed to static natural images and dynamic natural movie clips. The project was developed as part of the **Mathematical Modelling for Neuroscience** course at Università Bocconi.

## Authors

Cesare Bergossi, Riccardo Carollo, Emilija Milanovic, Elia Parolari, Giulia Pezzani

## Research Question

> Do visual stimuli that elicit similar neural responses in mice also share visual features?  
> If so, what are these defining characteristics?

## Repository Structure

```bash
neural-stimuli-similarity/
├── project.ipynb              # Main notebook with full analysis pipeline
├── report.pdf                 # Final report explaining methods, results, and conclusions
├── natural_scenes.pdf         # Reference for image stimuli shown to mice
├── data/
│   ├── channels.csv
│   ├── probes.csv
│   ├── sessions.csv
│   └── 798911424/
│       ├── metadata.npy
│       └── stimuli.csv
└── README.md
```

## Approach Overview

### Dataset

The data comes from the [Allen Brain Observatory – Visual Coding Dataset](https://observatory.brain-map.org/visualcoding). It includes:

- Spiking activity from the visual cortex of a 110-day-old female mouse
- Neural responses to:
  - **Natural Movie 1** (video sequence)
  - **Natural Scenes** (static grayscale images)
- Preprocessed to obtain average firing rates per unit per stimulus

### Analysis Pipeline

1. **Preprocessing**  
   - Spiketime data is converted into firing rates  
   - Neural responses are averaged across repeated presentations  
   - Log-transform and standardization applied to reduce noise and skewness

2. **Dimensionality Reduction**  
   - PCA used to project neural responses into a 3D latent space  
   - UMAP used for 2D visualization to capture nonlinear structure

3. **Clustering**  
   - HDBSCAN clustering identifies stimulus groups with similar neural responses  
   - Visual inspection of grouped images reveals shared visual properties (e.g. textures, orientation)

4. **Session Comparison**  
   - Repeated analysis across different sessions (and different mice) shows consistency  
   - Age and session variability had limited impact on results

## Key Insights

- Static images that produce similar neural responses often share **structural features** (contrast, textures, object orientation).
- Temporal stimuli (videos) produce **continuous response curves**, where context and preceding images affect spiking patterns.
- Dimensionality reduction + clustering offers an effective way to visualize high-dimensional neural data and extract visual correlates.

## Limitations & Future Work

- The dataset analyzed includes only one session's worth of clean data  
- Extension to more sessions and animals would improve generalizability  
- Deep learning-based feature extraction (e.g. VGG16) is proposed for better image similarity modeling
