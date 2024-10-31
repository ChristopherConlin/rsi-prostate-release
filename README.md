# rsi-prostate-release

## Requirements
1. Linux (Debian or RedHat derivative)
   - With python 3.something (for generating DICOM SEG files)
3. Version 9.12 (R2022a) of the MATLAB Runtime
4. Docker (to run the automated prostate segmentation)

## Installation instructions
### RSI software
1. Download latest **Release** from this repo
      - Look under "Releases" to the right of this page
      - Download both the rsiapp executable and the source code zip (or tar.gz)
3. Unzip the source code files onto your local filesystem, and place the rsiapp executable in the same directory

### MATLAB Runtime:
1. Download and install version 9.12 (R2022a) for 64-bit Linux: https://www.mathworks.com/products/compiler/mcr/index.html
   - See readme_rsiapp.txt file in this repo for more information

### Docker container
1. Obtain the Docker container from Cortechs.AI
2. Install according to the instructions provided in the prostate-seg-instructions.md file in this repo

### Python virtual environment
- Requirements for the python virtual environment are listed in the py_venv_requirements.txt file in this repo
```
virtualenv <env_name>
source <env_name>/bin/activate # (or activate.csh for (t)csh)
(<env_name>)$ pip install -r path/to/py_venv_requirements.txt
```

## Usage
1. Edit the params.txt file to configure runtime options
   - Be sure to provide the correct path to the python virtual environment if you intend to generate DICOM SEG files
3. Call the compiled MATLAB executable (see readme_rsiapp.txt):
```
./run_rsiapp.sh <absolute path to MATLAB Runtime> <absolute path to MRI DICOM data> <absolute path to directory for output files> <absolute path to params.txt file>
```
   - **Important:** Make sure to provide absolute paths (e.g., `/home/user/data` instead of `~/data`)
