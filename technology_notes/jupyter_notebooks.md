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
  