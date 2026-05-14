---
title: 'yabplot: yet another brain plot for unified neuroimaging visualization in Python'
tags:
  - Python
  - neuroimaging
  - visualization
  - neuroscience
  - 3D
authors:
  - name: Toomas Erik Anijärv
    orcid: 0000-0002-3650-4230
    affiliation: 1
affiliations:
 - name: Clinical Memory Research Unit, Department of Clinical Sciences Malmö, Faculty of Medicine, Lund University, Lund, Sweden
   index: 1
date: 11 May 2026
bibliography: paper.bib
---

# Summary

Neuroimaging analyses often produce results in several anatomical representations. A single study may include values defined in atlas-based regions, such as cortical parcels, subcortical structures, white-matter bundles, or connectivity matrices, as well as continuous voxel-wise and vertex-wise maps. Communicating these results requires figures that are anatomically interpretable, visually consistent, and reproducible from the same computational workflow used to generate the data.

`yabplot` (yet another brain plot) is an open-source Python package for creating three-dimensional neuroimaging visualizations across these representations. It provides a unified interface for plotting cortical parcellations, vertex-wise cortical data, voxel-wise volumetric data, subcortical structures, white-matter bundles, tractometry results, and connectome graphs. The package is intended for researchers who want to create publication-ready figures directly from Python scripts or Jupyter notebooks, without switching between multiple specialized graphical applications. Inputs depend on the function, but include NIfTI images, surface files, tractography files, arrays, dictionaries, and matrices, which are mapped to standard or user-defined anatomical resources.

The package builds on established scientific Python libraries. It uses `nibabel` for neuroimaging file input/output [@Brett:2024], `numpy` for numerical array operations [@Harris:2020], `pandas` for tabular and labelled data inputs [@McKinney:2010], `scipy` for interpolation, filtering, and sparse matrix operations [@Virtanen:2020], `pooch` for resource retrieval and caching [@Uieda:2020], `scikit-image` for extracting surface meshes from volumetric masks [@vanDerWalt:2014], `pyvista` for three-dimensional mesh representation, scene construction, and rendering [@Sullivan:2019], `trame` for interactive browser-based visualization [@Jourdain:2025], and `matplotlib` for static figure composition and customization [@Hunter:2007]. By combining these tools behind a compact plotting API, `yabplot` handles data mapping, mesh creation, camera placement, lighting, and rendering while retaining compatibility with standard Python plotting workflows.

![Overview of `yabplot` functionality. The package provides utilities for resource access, atlas construction, volume projection, and mesh handling, and high-level plotting functions for cortical parcellations, vertex-wise surface maps, subcortical structures, voxel-wise volumes, white-matter tracts, and connectome graphs.](figures/overview_joss.pdf)

# Statement of need

The neuroimaging visualization ecosystem includes many mature and widely used tools. Connectome Workbench supports surface-based visualization and Human Connectome Project resources [@Marcus:2011], MRtrix3 provides diffusion MRI processing and tractography visualization [@Tournier:2019], and BrainNet Viewer supports graph-based visualization of human connectomes [@Xia:2013]. In Python, Nilearn provides accessible statistical neuroimaging visualization, especially for slice-based, glass-brain, and machine-learning workflows [@Abraham:2014], while BrainSpace supports surface-based visualization in the context of macroscale gradients and connectomics [@VosdeWael:2020].

These tools cover important parts of the visualization workflow, but producing a coherent figure that combines different representations of neuroimaging data can still require several packages or applications. This introduces practical barriers. Researchers may need to translate data between different input conventions; manual screenshot-based workflows make figure generation harder to reproduce; and differences in lighting style and camera perspective can make results appear visually inconsistent within the same research study.

`yabplot` addresses this gap by focusing on unified, scriptable, publication-oriented 3D rendering of common neuroimaging result types within a single Python environment. Its plotting functions follow a shared pattern: users provide data values and an anatomical target, choose views and visual styling, and receive a rendered figure or interactive object. High-level functions are provided for regional cortical data (`plot_cortical`), vertex-wise cortical data (`plot_vertexwise`), voxel-wise volumes (`plot_voxelwise`), subcortical structures (`plot_subcortical`), white-matter bundles (`plot_tracts`), and connectivity matrices (`plot_connectome`). These functions share common building blocks for data mapping, mesh construction, camera presets, color handling, background anatomy for context, and output generation, while still exposing modality-specific options where needed.

A further design goal is to separate the Python package from large anatomical resources. `yabplot` retrieves supported atlases, meshes, and tract resources on demand and caches them locally, keeping the core installation lightweight while making resource use explicit. The package also supports custom user-defined anatomical resources through atlas-building and mesh-construction utilities, allowing users to adapt the workflow to study-specific parcellations, segmentations, and tractography datasets. By bringing these visualization tasks into a consistent interface, the package lowers the technical barrier to high-quality 3D neuroimaging figures and supports reproducible scientific communication.

# AI usage disclosure

Generative AI models have been utilized in the development process of `yabplot` and in the drafting of this manuscript. The author reviewed and verified all AI-generated content.

# Acknowledgements

The author would like to thank the early contributors, including Anthony J Barrows, Jannis Denecke, and Anthony Gagnon, for their valuable code improvements and feedback during the development of this package. `yabplot` relies on the work of the broader neuroimaging and scientific Python communities, including the developers and maintainers of `nibabel`, `numpy`, `scipy`, `pandas`, `pyvista`, `trame`, `matplotlib`, `pooch`, `scikit-image`, and the atlas resources supported by the package. Users should cite the original publications for any atlases used in their analyses.

# References
