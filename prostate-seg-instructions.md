
## Load the docker image

* prerequisites: a unix system with docker desktop. In a terminal, you should be able to run `docker images` to see a list of your images.
* unzip the tarball: `gzip -d prostate-seg.tar.gz`. This should produce a new file `prostate-seg.tar`
* load the tar'ed image into docker `docker load -i prostate-seg.tar`. This will take a while, about 5 minutes on my laptop. To check that the image imported correctly, run `docker images`. You should see the  image `696021503801.dkr.ecr.us-east-1.amazonaws.com/prostate-segmentation` with tag `dev`.

## Run the docker image

The command to execute the app is:

    docker run -i --rm -u 0:0 -v /full/path/to/input_dir:/input:ro -v /full/path/to/output_dir:/output 696021503801.dkr.ecr.us-east-1.amazonaws.com/prostate-segmentation:dev

You should replace `/full/path/to/input_dir` and `/full/path/to/output_dir` to the full absolute paths to the input and output directories, respectively. To reference a relative path, you can use `$(pwd)`, e.g. `-v $(pwd)/path/relative/to/current/dir`.

Inputs are expected to be T2-weighted images of the prostate in one of the following formats: `.mgz`, `.mgh`, `.nii`, `.nii.gz`. DICOM series will probably work, but this hasn't been tested and is not recommended. *The input directory should contain only medical image files*. All compatible image files in the input directory will be segmented and the outputs will be written to the output directory. The output images will have the suffix `_seg` appended to the input filename, so it is okay to use the same directory for input and output.

### Run on sample image

Included in this folder is a prostate T2 image in `.mgh` format. Run the app on this file by changing to the `sample_image` directory and running:

    docker run -i --rm -u 0:0 -v $(pwd):/input:ro -v $(pwd):/output 696021503801.dkr.ecr.us-east-1.amazonaws.com/prostate-segmentation:dev

It should complete in a few seconds and produce the new segmentation file `sample_image/prostate_T2_seg.mgh`.
