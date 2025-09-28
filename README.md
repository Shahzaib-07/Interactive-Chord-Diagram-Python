# Interactive Chord / Network Visualizer in Python

An interactive chord / network diagram tool built with **HoloViews** + **Panel**, offering live filtering, node ordering, network toggling, and more. While designed with **fMRI / functional connectivity (FC)** in mind, it works with **any symmetric weighted network** from diverse domains.

---

## Features

- Live threshold filtering: adjust minimum absolute weight to hide weak edges  
- Top-K filtering: display only the strongest network pairs  
- Focus on or exclude specific networks  
- Order nodes by total connectivity strength  
- Show / hide isolated networks (with no strong edges)  
- Toggle visibility of modules / networks  
- Interactive hover, click, and tooltips powered by Bokeh + Panel  
- Easy embedding in Jupyter notebooks or as standalone Panel apps  

---

## Installation & Setup

```bash
pip install numpy pandas holoviews panel
```

### In your notebook or Python environment, enable the extensions:
```bash
import holoviews as hv; import panel as pn
hv.extension('bokeh')
pn.extension('bokeh')
```


### Example
```bash
import numpy as np
from your_module import chord_by_network_UI  # adjust import path as needed

# Create dummy symmetric matrix (e.g. correlation / connectivity)
n = 8
A = np.random.uniform(-1, 1, size=(n, n))
A = (A + A.T) / 2
np.fill_diagonal(A, 1.0)

# Assign nodes to network labels
networks = np.array(['NetA', 'NetA', 'NetB', 'NetB', 'NetC', 'NetC', 'NetD', 'NetD'])

# Launch the interactive UI
app = chord_by_network_UI(A, networks, default_title="Dummy FC Chord")
server = app.show(threaded=True, title="Interactive Chord Viewer")
```

## fMRI Data Example
![My Tool Screenshot](/images/Chord1.PNG)
![My Tool Screenshot](/images/Chord2.PNG)

## Gene Co-expression Data Example
![My Tool Screenshot](/images/Gene_.PNG)

Once launched, you can:
- Adjust Min |FC| to filter out weak edges
- Change Top-K to limit number of shown pairs
- Focus on particular networks
- Toggle order or hide isolated networks
- Interact with the chord diagram via hover / click

## Applicability Across Domains

Though motivated by fMRI / brain connectivity, this tool is applicable to many domains involving symmetric (undirected) weighted networks. Some examples:

- Neuroscience / Brain Networks – functional connectivity among brain regions
- Social Networks – strength of associations or interactions between groups
- Gene Co-expression / Biology – correlations among genes or proteins
- Text / Linguistics – word co-occurrence or similarity networks
- Economics / Trade – correlations or flows among sectors or regions
- Ecology / Species Interactions – strength of interactions, symbioses, etc.

Because of thresholding, focus, and ordering controls, the tool helps reveal the “backbone” or module structure of such networks.

## License & Attribution

This project is released under a permissive license with required attribution.
If you use or adapt this tool publicly (e.g. in a paper or repository), kindly cite:

Interactive Chord / Network Visualizer by Muhammad Shahzaib, 2025.

Additionally, if your work is in the fMRI / neuroimaging domain, you may mention that context in your publication or documentation.

## Contact & Support

If you discover bugs, want to request features, or have questions, please open an issue or reach me at m.shahzaib07@gmail.com
