
# Recent Updates & Important Notes

We are constantly working to improve the Ultralytics ecosystem. This document highlights recent enhancements and provides important notes for our users and contributors.

## Enhanced Mask Saving for Segmentation and Tracking

We have implemented a significant improvement to the mask-saving functionality for both segmentation and tracking tasks. When using the `save_mask=True` argument during prediction, the framework now correctly saves cropped images of individual objects with a transparent background.

This feature is particularly useful for workflows that require isolated object images for further analysis, dataset creation, or other downstream tasks. The saved images are in PNG format to preserve transparency.

**How it works:**
The `predictor` now intelligently handles masks from segmentation and tracking results, scales them to the original image size, and saves each object as a separate PNG file. For tracking, you can control whether to save a mask for every frame or only the first time a track ID appears.

For a detailed guide on how to leverage this feature, please see our documentation on Isolating Segmentation Objects.

## Video Saving and Codec Support (`avc1`)

Our video writing functionality now defaults to the `avc1` (`.mp4`) codec on macOS and Linux systems to ensure high-quality output and broad compatibility.

**Important:** To ensure the `avc1` codec is available for video saving, we strongly recommend installing `opencv` from the `conda-forge` channel. The version of `opencv-python` installed via pip may not include all necessary video codecs. This can be done after installing the `ultralytics` package.

To set up your environment correctly for video processing:

```bash
# Install the ultralytics package from PyPI
pip install ultralytics

# Install OpenCV from conda-forge to get full video codec support
conda install -c conda-forge opencv
```

For more details on setting up with Conda, refer to our Conda Quickstart Guide.

## Recommended Installation for Developers

For developers and contributors who wish to work with the latest source code or make modifications, we recommend installing the package in "editable" mode. This method links the installed package to your local source code, so any changes you make are immediately effective without needing to reinstall.

After cloning the repository, navigate to the directory and run:

```bash
# Navigate to your cloned ultralytics repository
cd ultralytics

# Install in editable mode
pip install -e .
```

This is the preferred method for setting up a development environment. For standard users, `pip install ultralytics` remains the recommended approach. More installation options can be found in our Quickstart Guide.
