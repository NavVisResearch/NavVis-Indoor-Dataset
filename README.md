# TUM LSI Dataset
The TU Munich Large-Scale Indoor (TUM LSI) Dataset was introduced and used for evaluation in [Walch et al. (2017)](https://github.com/NavVisResearch/NavVis-Indoor-Dataset#citation) for image-based localization.

#### Deep learning for image-based indoor localization
Introducing LSTMs for structured feature correlation, Walch et al. use TUM LSI data in order to train and evaluate deep learning approaches for image-based indoor localization. Their results show that learning-based approaches are on par with, or even outperform, traditional local-feature-based methods.

#### TUM LSI Data
TUM LSI is a subset of NavVis Indoor Dataset (see below). It comprises 1,314 high-resolution images, covering 5,575 m<sup>2</sup> of one entire floor of a university building.

* Within NavVis Indoor Dataset, the scan ID for TUM LSI Dataset is `2015-08-16_15.34.11`.
* Please note that Walch et al. used only cameras `cam0` through `cam4` (i.e. skipping the upwards-facing camera at each capture location), resulting in a total of 1,095 images used for evaluation in the paper.
* The partitioning into training and test sets as used by Walch et al. can be found in the files `tum-lsi_train.txt` and `tum-lsi_test.txt`.
* Note that images are stored in portrait format and were not rotated. For preparing the images, Walch et al. followed [1, section 3.2] and first rescaled horizontally to 256 pixels, then performed random crops to 224x224.

[1] A. Kendall, M. Grimes, and R. Cipolla. Posenet: A convolutional network for real-time 6-dof camera relocalization. In IEEE International Conference on Computer Vision (ICCV), 2015


# NavVis Indoor Dataset (setup in progress)
_An extensive collection of geo-referenced images from large-scale indoor spaces_

* More than 50,000 high-resolution images (still images, not video frames)
* Covering more than 50,000 m<sup>2</sup> of 12 different buildings at Technical University of Munich
* Extrinsic poses for all images in a geo-referenced coordinate system
* Recorded between August 2015 and March 2016
* Large variety of indoor spaces (e.g. architectural styles and lighting conditions)

## How To Get The Images
If you would like to receive access to NavVis Indoor Dataset or TUM LSI Dataset images, please fill out and submit this [form](https://forms.office.com/Pages/ResponsePage.aspx?id=CSDLYH24P02GUqS9O9H4ZDDJ0Rkk_VBEhj8bcLfAkNdURjJaTU9MVlZJSk1PODgxQU5IQVJBUkFUSS4u) in which you agree to the [NavVis Indoor Dataset End-User License Agreement](http://www.navvis.com/uploads/docs/EULA_Dataset_EN.pdf).

## Data Organization
* The dataset is organized by individual contiguous scans.
* Images and corresponding poses are stored in separate directory structures called `images` and `poses`.
* Each scan is identified by its unique timestamp `<scan_timestamp>`.
* The `images` directory contains a subdirectory for each scan named `<scan_timestamp>` which stores all corresponding images.
* Images are grouped in sets of six. Each set was taken at the same time and (roughly) at the same _capture location_. The six images per set are numbered `cam0` to `cam5`.
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

|-- geo-refrence.xml // Global geo-reference of root node and 
|                    // coordinate transformations to indiviual scan coordinate systems
|
poses
|
|-- <scan_timestamp>_poses.xml // Pose coordinates of all images in the scan with name <scan_timestamp>
|-- <scan_timestamp>_poses.xml
|-- <scan_timestamp>_poses.xml
...
```

## Data Formats
NavVis Indoor Dataset is comprised of images and corresponding extrinsic poses.

#### Images
- File format: jpeg
- Image size: 4592 × 3448 pixels

#### Poses
Poses are specified by way of a transformation tree: The root of the tree is a global geo-reference in WGS84 coordinates. The root spans a local metric coordinate system in which the various scan coordinate systems are specified. Each scan, in turn, spans its own coordinate system, in which corresponding image poses are given.

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
  - 3D translation specifying the image position in its dataset frame: 3x1 vector (x,y,z)
  - 3D rotation specifying the image orientation in its dataset frame: 4x1 quaternion (w,x,y,z)

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
NavVis Indoor Dataset and TUM LSI Dataset are provided under the [NavVis Indoor Dataset End-User License Agreement](http://www.navvis.com/uploads/docs/EULA_Dataset_EN.pdf).

## Support
If you need help with anything, please contact us at research@navvis.com
