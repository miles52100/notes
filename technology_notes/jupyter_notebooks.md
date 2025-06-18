# Jupyter Labs and Notebooks

## Kernels

To list available kernels

`jupyter kernelspec list`

To create a new kernel

  1. Activate conda-env or venv (this will be what the kernel uses)
  2. Install ipykernel 
    `conda install ipykernel`
  3. Install the kernel
    `kernel install --user --name=<any-name>`
  4. Deactivate your conda, venv environment
  5. Restart Jupyter lab/notebook

To delete an unwanted kernel

  1. `jupyter kernelspec uninstall unwanted-kernel`
  


## Anaconda and licence issues

This [article](https://www.datacamp.com/blog/navigating-anaconda-licensing) by datacamp.com has a nice explanation of what is changing.
Essentially, you cannot use the default channels without a licence. These channels are curated and maintained for stability by Anaconda. So, if you're an org with >200 users
then they now want to charge for using these default chnnels.

You can still use the conda package and environment manager, provided you use open source channels such as conda-forge.

### Changes to AC

I've installed the `JupyterLab` application from the AC cloud store.
Clicking on the top right option of this application allows for managing kernel envirnoments.
You have the option of both conda environments and virtualenv.

You need a base Python to build from.
I have:

  * v3.9.21 located in `/opt/anaconda3/bin/python`
  * v3.13 (downloaded from AC cloud store) located in `/usr/local/bin/python3`

My conda environments (run `conda env list`) are located in `/opt/anaconda3/envs/`.

Using the JupterLab app, you can create a new virtual env clicking the top right (3 horizontal bars icon) and manage environments option.
You need to point to the base Python (I have set this to v3.13, see above).
It then creates a virtual environment, currently the default location is
`Users/<me>/Library/jupyterlab-desktop/envs/`.
It has a default `env_1` for the name.

Selecting such an evironment is for the **JupyterLab server kernel**. Opening a terminal in the JupyterLab app doesn't mean that terminal is configured to use that virtual environment. To enable that you must activate the environment in the terminal session.

Activating a virtual environment using the terminal:

  * To activate `source /Users/<me>/Library/jupyterlab-desktop/envs/<env-name>/bin/activate`
  * To deactivate `deactivate`
  * To delete, after deactivating, `rm -r Users/<me>/Library/jupyterlab-desktop/envs/<env-name>`
