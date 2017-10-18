# NavVis Indoor Dataset
An extensive research dataset of geo-referenced images from large-scale indoor spaces

# TUM LSI Dataset
The TU Munich Large-Scale (TUM LSI) Dataset was introduced and used for evaluation in Walch et al. (2017).

TUM LSI is a subset of NavVis Indoor Dataset covering part of a Technical University of Munich (TUM) office building.

# Data Organization
The dataset is organized by individual contiguous scans. Images and corresponding poses are stored in separate directory structures. Each scan is identified by its unique timestamp (`<scan_timestamp>`) and is stored in a separate folder named `<scan_timestamp>`.

# Data Formats

### Images
- File format: jpeg
- Image resolution: 3448 x 4592 pixels

### Poses
- File format: xml
- 3D translation: 3x1 vector, double precision
- 3D rotation: 4x1 quaternion, double precision
- Global geo-reference: WGS84

# Citation
If you use the NavVis Indoor Dataset or the TUM LSI Dataset, please cite:
```
@InProceedings{walch17spatialstms,
 author = "Florian Walch and
           Caner Hazirbas and
           Laura Leal{-}Taix{\'{e}} and
           Torsten Sattler and
           Sebastian Hilsenbeck and
           Daniel Cremers",
 title = "Image-based localization using LSTMs for structured feature correlation",
 month = "October",
 year = "2017",
 booktitle = "IEEE International Conference on Computer Vision (ICCV)",
 url       = {http://arxiv.org/abs/1611.07890}
}
```

# Changelog

# License

# Support
