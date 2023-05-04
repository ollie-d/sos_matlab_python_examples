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
3. Create an environment for MATLAB in miniconda and activate
  - ```conda create -n "sos" python=3.10```
  - ```conda activate sos```
4. Point MATLAB to your conda environment
  - ```pyversion('C:\Users\<user>\miniconda3\envs\matlab\python.exe');```
  - ```pyenv('ExecutionMode', 'OutOfProcess');```
5. Follow basic setup of SoS with anaconda
  - link: https://vatlab.github.io/sos-docs/running.html#Conda-installation
  - Install the Python sos kernels
<!--
6. Follow video setup of installing MATLAB kernel for jupyter
  deviation: The video is old and does not provide the correct way of install the matlab environment. Follow the steps here:
    - link: https://www.mathworks.com/help/matlab/matlab_external/install-the-matlab-engine-for-python.html
    - (note for above: make sure you activate your virtual env so as not to use a potential global python env)
7. Continue the video setup by executing:
  - ```python -mimatlab install```
    - This should result in a success
-->
6. Install the MATLAB engine to Python (note that official documentation is deprecated on MathWorks and SoS websites now)
  - In conda run: `python -m pip install matlabengine==9.13.7`
  - To test that this worked execute the following code:
    - ```import matlab.engine```
    - ```eng = matlab.engine.start_matlab()```
    - ```eng.isprime(37)```
      - This should return ```True```. If there were errors, troubleshoot at https://github.com/mathworks/matlab-engine-for-python
    - Exit Python with ```exit()``` but keep terminal open.
7. Install imatlab
  - ```pip install imatlab```
8. Install SoS MATLAB Subkernel
  - ```pip install sos-matlab```
9. Finish installation by installing mimatlab (required administrator privledge)
  - If you did not open your terminal with elevated access, please do so now and re-activate sos via ```conda activate sos```
  - ```python -mimatlab install```
10. Confirm that the installation works by running the example/test_installation notebook and running each cell.

## Notes:
1. You will need to change the ratelimit for Jupyter to visualize larger EEGLAB objects. Follow the steps here:
    - https://stackoverflow.com/questions/43288550/iopub-data-rate-exceeded-in-jupyter-notebook-when-viewing-image
    - ```jupyter notebook --generate-config```
        - edit this file
        - search for ```c.NotebookApp.iopub_data_rate_limit```
        - uncomment this and set the value to: ```=1.0e10```
