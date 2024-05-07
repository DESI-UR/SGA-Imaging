# SGA-Imaging
Galaxy similarity analysis and large-galaxy finding for the extension of the SGA.

## Installing ssl environment
The following instructions are for installing the `ssl` environment at NERSC, but can likely be used as a guide for installation on other systems.
1. Clone the `ssl-legacysurvey` repository: https://github.com/georgestein/ssl-legacysurvey
2. Download mamba (NERSC likely has mamba available, but downloading it ourselves makes sure that the `pip` it uses while building the environment has the correct permissions, to avoid getting various permission errors that we received while trying to install this environment as recommended by the original `ssl` repo.): In your home directory, run
   ```
   wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
   ```
3. Change the mamba file's permissions so that we can run the file to install it: Still in your home directory, run
   ```
   chmod +x Miniforge3-Linux-x86_64.sh
   ```
4. Install mamba:
   ```
   ./Miniforge3-Linux-x86_64.sh
   ```
5. Update your `.bashrc` file to add the path to mamba (so that the terminal knows where to look when we type `mamba` into the terminal).  To do this, first open the `.bashrc` file:
   ```
   vi ~/.bashrc
   ```
   In the file, type `i` to enter insert mode.  Go to the bottom of the file, and add the line
   ```
   export PATH=$HOME/miniforge3/bin:$PATH
   ```
   To save and exit vi, hit the `esc` button on your keyboard, followed by `wq`.  Then hit `Enter`.
6. Refresh the terminal with the new `.bashrc` file by running
   ```
   source ~/.bashrc
   ```
   in the terminal.
7. Change directories into the `ssl-legacysurvey` directory:
   ```
   cd ssl-legacysurvey
   ```
8. Edit the `environment.yml` file to put the environment into your mamba folder.  Open the file and change the last line to read
   ```
   prefix: ${HOME}/miniforge3/envs/ssl-pl
   ```
9. In the terminal, run
   ```
   mamba env create -f environment.yml
   ```
10. We now need to install the `ssl-legacysurvey` python module in our new environment.  To do this, run the following two commands in the terminal:
    ```
    source activate ssl-pl
    python setup.py install
    ```
11. Finally, to add the environment to the jupyter kernals, run the following in the terminal:
    ```
    python -m ipykernal install --user --name ssl-pl --display_name ssl-pl
    ```
