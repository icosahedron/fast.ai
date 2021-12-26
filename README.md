# Fast.ai Lessons

I am working through the `fast.ai` lessons found at the [Fast Book](https://github.com/fastai/fastbook) Github repo.

There are several good recommendations for where to perform the exercises for free with a GPU, but I wanted to do some stuff with sensitive workplace data, so I needed a local installation.  And we use Windows and .NET, so my primary development system is Windows.  Using CUDA in WSL or VMs is fairly difficult, so I'm using the base installation of Windows.  (This of course assumes that you have an NVidia GPU with CUDA installed.  See NVidia for instructions on installing CUDA.)

## Local Installation

To make things easier, I've made a local installation of `conda` and `pytorch` and friends, so I can run the notebook locally, but able to uninstall it easily if necessary.

```
pwsh.exe -Command Start-Process .\Anaconda3-2021.11-Windows-x86_64.exe -ArgumentList "/S","/InstallationType=JustMe","/AddToPath=0","/RegisterPython=0","/D=$(PWD)\anaconda" -Wait
```

This should install Anaconda into the directory you're in, into the `anaconda` subdirectory.

To test the notebook server runs properly, try the following command.

```
.\anaconda\condabin\conda.bat run jupyter notebook --no-browser --ip=0.0.0.0 --port=9999 --config=.\jupyter_notebook_config.json
```

Visit `https://localhost:9999` to see the password prompt.

The `jupyter_notebook_config.json` file is configured to provide password access using the password "Deep Learning from Scratch".  You should change the password to the hash per the instructions at [Securing a Notebook Server](https://jupyter-notebook.readthedocs.io/en/stable/public_server.html#securing-a-notebook-server)

Close the browser and exit the notebook server with `^C`.

## Install Pytorch and friends

Use the installed conda command to install the necessary libraries used.

```
.\anaconda\condabin\conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

## Uninstall Anaconda

To uninstall Anaconda, you should use the built in utility.  Despite being local, the installation actually does register with Windows Apps & Features.

```
.\anaconda\Uninstall-Anaconda.exe /S
```

This should completely remove Anaconda from your system.

## Lessons

The lessons are kept in the `notebooks` directory.
