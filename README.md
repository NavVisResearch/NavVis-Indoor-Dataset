# NavVis Indoor Dataset
_An extensive research dataset of geo-referenced images from large-scale indoor spaces_

**Please note: this page is still work in progress**

NavVis Indoor Dataset is coming soon. For now, please refer to the TUM LSI Dataset.

# TUM LSI Dataset
The TU Munich Large-Scale Indoor (TUM LSI) Dataset was introduced and used for evaluation in Walch et al. (2017).

TUM LSI is a subset of NavVis Indoor Dataset. It comprises 1314 images covering 5575 square-meters of an entire floor level at Technical University of Munich (TUM).

# How To Get The Data
If you would like to get access to NavVis Indoor Dataset or TUM LSI Dataset, please download the agreement to the NavVis Indoor Dataset Terms of Use and send a filled in and signed copy of it to research@navvis.com.

# Data Organization
* The dataset is organized by individual contiguous scans.
* Images and corresponding poses are stored in separate directory structures called `images` and `poses`.
* Each scan is identified by its unique timestamp (`<scan_timestamp>`) and is stored in a separate subdirectory named `<scan_timestamp>`.
* The `images` directory contains for each scan its corresponding images grouped in sets of six.
* The six images in a set have been taken at the same time and (roughly) same _trigger location_ and are numbered from `cam0` to `cam5`.
* The total number of _trigger locations_ varies per scan. _Trigger locations_ are numbered starting from `00000`.

The directory structure is as follows:
```
images
|-- <scan_timestamp>
|   |-- 00000-cam0.jpg // first image of first trigger location
|   |-- 00000-cam1.jpg
|   |-- 00000-cam2.jpg
|   |-- 00000-cam3.jpg
|   |-- 00000-cam4.jpg
|   |-- 00000-cam5.jpg // last image of first trigger location
|   |-- 00001-cam0.jpg // first image of second trigger location
|   |-- 00001-cam1.jpg
|   |-- 00001-cam2.jpg
|   |-- 00001-cam3.jpg
|   |-- 00001-cam4.jpg
|   |-- 00001-cam5.jpg // last image of second trigger location
|   ...
|
|-- <scan_timestamp>
|   |-- 00000-cam0.jpg
|   |-- 00000-cam1.jpg
|   |-- 00000-cam2.jpg
|   |-- 00000-cam3.jpg
|   |-- 00000-cam4.jpg
|   |-- 00000-cam5.jpg
|   ...
|
|-- <scan_timestamp>
...

poses
|-- geo-refrence.xml
|
|-- <scan_timestamp>
|   |-- poses.xml
|
|-- <scan_timestamp>
|   |-- poses.xml
|
|-- <scan_timestamp>
...
```

# Data Formats
The NavVis Indoor Dataset comprises images and their extrinsic poses.

### Images
- File format: jpeg
- Image resolution: 3448 x 4592 pixels

### Poses
Poses are specified by way of a transformation tree. The root of the tree is a global geo-reference in WGS84 coordinates. The root spans a metric coordinate system in which the individual scan coordinate systems are specified by way of a relative translation and rotation transofrmation. Each scan, in turn, spans its own coordinate system in which the corresponding image poses are given.

- File format: xml
- Global geo-reference: WGS84
- Poses: 6 degrees of freedom
  - 3D translation: 3x1 vector
  - 3D rotation: 4x1 quaternion

# Citation
If you use the NavVis Indoor Dataset or the TUM LSI Dataset, please cite:
```
@InProceedings{walch17spatiallstms,
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
If you need help with anything please contact us via research@navvis.com
