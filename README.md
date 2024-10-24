# rsi-prostate-release

## Requirements
1. Linux (Debian or RedHat derivative)
   - With python 3.something (for generating DICOM SEG files)
3. Version 9.12 (R2022a) of the MATLAB Runtime
4. Docker (to run the automated prostate segmentation)

## Installation instructions
### RSI software
1. Download latest release from this repo
2. Unzip files onto your local filesystem

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
2. Call the compiled MATLAB executable:
`./run_prostate_app.sh <path to MATLAB Runtime> <path to MRI DICOM data> <path to directory for output files> <path to params.txt file>`
e.g.,
`./run_prostate_app.sh /space/bil-syn01/1/cmig_bil/v912 /home/ccconlin/PDS3412 /home/ccconlin/test_out/ ./params.txt`

