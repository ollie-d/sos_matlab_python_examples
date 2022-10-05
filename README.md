# SoS MATLAB x Python3 Examples

Here are the tools I'm using

- OS: Windows 11
  - Terminal launching Miniconda3 (4.12.0)

- Python: 3.10.4
- pip: 22.2.2
- MATLAB: R2022b (9.13.0.2049777 )

## Installation Steps
1. Install and activate MATLAB
2. Install miniconda3 or anaconda3 (I use miniconda)
3. Create an environment for MATLAB in miniconda
  - ```conda create -n "matlab" python=3.10```
4. Point MATLAB to your conda environment
  - ```pyversion('C:\Users\<user>\miniconda3\envs\matlab\python.exe');```
  - ```pyenv('ExecutionMode', 'OutOfProcess');```
5. Follow basic setup of SoS with anaconda
  - link: https://vatlab.github.io/sos-docs/running.html#Conda-installation
  - Install the Python and MATLAB sos kernels
6. Follow video setup of installing MATLAB kernel for jupyter
  deviation: The video is old and does not provide the correct way of install the matlab environment. Follow the steps here:
    - link: https://www.mathworks.com/help/matlab/matlab_external/install-the-matlab-engine-for-python.html
    - (note for above: make sure you activate your virtual env so as not to use a potential global python env)
7. Continue the video setup by executing:
  - ```python -mimatlab install```
    - This should result in a success

## Notes:
1. You will need to change the ratelimit for Jupyter to visualize larger EEGLAB objects. Follow the steps here:
    - https://stackoverflow.com/questions/43288550/iopub-data-rate-exceeded-in-jupyter-notebook-when-viewing-image
    - ```jupyter notebook --generate-config```
        - edit this file
        - search for ```c.NotebookApp.iopub_data_rate_limit```
        - uncomment this and set the value to: ```=1.0e10```