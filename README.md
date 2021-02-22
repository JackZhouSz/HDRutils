# HDRutils-pip

Some utility functions to generate HDR images from a sequence of exposure time or gain modulated images.

## Installation
To download HDRUtils, either fork this github repo or simply use Pypi via pip:

    pip install HDRutils

You will need the [FreeImage plugin](https://imageio.readthedocs.io/en/stable/format_exr-fi.html) for reading and writing OpenEXR images:

    imageio_download_bin freeimage

## Usage
Just import HDRutils and call the required functions

### Merge input images
The [rawpy](https://github.com/letmaik/rawpy) wrapper is used to read RAW images. [Noise-aware merging](https://www.cl.cam.ac.uk/research/rainbow/projects/noise_aware_merging/) is performed using the Poisson-noise optimal estimator. The generated HDR image is linearly related to the scene radiance

```python
import HDRutils

files = ['file1.dng', 'file2.dng', 'file3.dng']		# RAW input files
HDR_img = HDRutils.imread_merge(files)
HDRutils.imwrite('merged.exr', HDR_img)
```

### Deghosting
TODO

## Citation
If you find this package useful, please cite

    @inproceedings{hanji2020noise,
      title={Noise-Aware Merging of High Dynamic Range Image Stacks Without Camera Calibration},
      author={Param Hanji and Fangcheng Zhong and Rafal K. Mantiuk},
      year={2020},
      booktitle={Computer Vision - {ECCV} 2020 Workshops - Glasgow, UK, August 23-28, 2020, Proceedings, Part {III}},
      url={https://doi.org/10.1007/978-3-030-67070-2\_23}
    }