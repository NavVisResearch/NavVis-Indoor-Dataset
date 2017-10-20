# NavVis Indoor Dataset
_An extensive collection of geo-referenced images from large-scale indoor spaces_

* 60,000 high-resolution images (still images not video frames).
* Covering more than 50,000 m^2 of 12 different buildings at Technical University of Munich.
* Extrinsic poses for all images in a geo-referenced coordinate system.
* Recorded between August 2015 and March 2016.
* Large variety of indoor scenes characteristics ranging from different architectural styles to varying capture conditions (e.g. scene illumination).

## TUM LSI Dataset
The TU Munich Large-Scale Indoor(TUM LSI) Dataset was introduced and used for evaluation in [Walch et al. (2017)](https://github.com/NavVisResearch/NavVis-Indoor-Dataset#citation).

#### Deep learning for image-based indoor localization
Introducing LSTMs for structured feature correlation, Walch et al. use TUM LSI data in order to train and evaluate deep learning approaches for image-based indoor localization. Their results demonstrate performance on par with, or even outperforming, traditional local-feature-based methods.

#### TUM LSI Data
TUM LSI is a subset of NavVis Indoor Dataset. It comprises 1314 high-resolution images, covering 5575 m^2 of one entire floor level at Technical University of Munich.

* Within NavVis Indoor Dataset, the scan ID for TUM LSI Dataset is `2015-08-16_15.34.11`.
* Please note that Walch et al. used only cameras `cam0` through `cam4` (i.e. skipping the upwards-facing camera at each capture location), resulting in a total of 1095 images used for evaluation.

## How To Get The Images
If you would like to get access to NavVis Indoor Dataset images or TUM LSI Dataset images, please download the agreement to the NavVis Indoor Dataset Terms of Use and send a filled in and signed copy of it to research@navvis.com.

## Data Organization
* The dataset is organized by individual contiguous scans.
* Images and corresponding poses are stored in separate directory structures called `images` and `poses`.
* Each scan is identified by its unique timestamp `<scan_timestamp>`.
* The `images` directory contains for each scan a subdirectory named `<scan_timestamp>` and, within this subdirectory, all corresponding images.
* Images are grouped in sets of 6. Each set was taken at the same time and (roughly) the same _capture location_. The six images in one set are numbered from `cam0` to `cam5`.
* The total number of _capture locations_ can vary per scan. They are numbered starting from `00000`.

The complete directory structure is as follows:
```
images
|-- <scan_timestamp>
|   |-- 00000-cam0.jpg // first image of first capture location
|   |-- 00000-cam1.jpg
|   |-- 00000-cam2.jpg
|   |-- 00000-cam3.jpg
|   |-- 00000-cam4.jpg
|   |-- 00000-cam5.jpg // last image of first capture location
|   |-- 00001-cam0.jpg // first image of second capture location
|   |-- 00001-cam1.jpg
|   |-- 00001-cam2.jpg
|   |-- 00001-cam3.jpg
|   |-- 00001-cam4.jpg
|   |-- 00001-cam5.jpg // last image of second capture location
|   |-- 00002-cam0.jpg
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
|-- geo-refrence.xml // Geo-reference of root node and 
|                    // coordinate transformations to indiviual scan coordinate systems
|
|-- <scan_timestamp>_poses.xml // Pose coordinates of all images in the scan with name <scan_timestamp>
|-- <scan_timestamp>_poses.xml
|-- <scan_timestamp>_poses.xml
...
```

## Data Formats
NavVis Indoor Dataset comprises images and correpsonding extrinsic poses given in a geo-referenced coordinate system.

#### Images
- File format: jpeg
- Image size: 3448 × 4592 pixels
- Image orientation: see [Exif](https://en.wikipedia.org/wiki/Exif)
- Image DPI: 180 pixels/inch
- Color space: sRGB

#### Poses
Poses are specified by way of a transformation tree. The root of the tree is a global geo-reference in WGS84 coordinates. The root spans a metric coordinate system in which the individual scan coordinate systems are specified by way of a relative translation and rotation transformation. Each scan, in turn, spans its own coordinate system in which corresponding image poses are given.

- File format: xml
- Global geo-reference (root node): WGS84
  - Longitude, latitude, height above ground, 1D rotation (yaw angle)
- Scan coordinate systems:
  - 6DoF transformation w.r.t. root node
  - 3D translation: 3x1 vector (x,y,z)
  - 3D rotation: 4x1 quaternion (w,x,y,z)
- Image poses:
  - 6DoF transformation w.r.t. scan coordinate system
  - Extrinsic parameters only
  - 3D translation: 3x1 vector (x,y,z)
  - 3D rotation: 4x1 quaternion (w,x,y,z)

## Citation
If you use NavVis Indoor Dataset or TUM LSI Dataset, please cite:
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

## Changelog


## License


## Support
If you need help with anything, please contact us at research@navvis.com
