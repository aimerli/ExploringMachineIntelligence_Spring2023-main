# Installing Python Coding Tools on Your Machine

To get started running Python on your machine, follow these steps:

## 1. Install miniconda or miniforge (depending on your machine)

We will be using conda, a package and environment manager for Python. To get conda, you'll be installing either Miniconda or Miniforge, depending on your system type. Your installation will give you Python, as well as some useful packages that you’ll need, as well as a way for you to manage and switch between different python environments (more on that later), and install new packages and libraries.

### a. How do I know if I have conda installed already?

#### Mac or Linux Users

Open up a Terminal and type ``which conda``. If you see something like "conda not found," it's not installed. Otherwise, skip to Step 2.

#### Windows Users

Open up a Terminal and type ``where conda``. If you see something like "conda not found," it's not installed. Otherwise, skip to Step 2.

### b. Installing Miniconda/Miniforge 

#### Mac Users

* Is your Mac an M1 or M2 machine? ([Here's how to check](https://www.howtogeek.com/706226/how-to-check-if-your-mac-is-using-an-intel-or-apple-silicon-processor/).) If so, do the following:
   * Download miniforge from [here](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh)
   * Then, open a Terminal window and navigate to the place where you downloaded this file. (For instance, if you saved it to your Downloads folder, you can type `cd ~/Downloads` and hit Return.)
   * Then, run the following commands, one by one, in Terminal, to install miniforge:
      * `xcode-select --install`
      *  `chmod +x Miniforge3-MacOSX-arm64.sh`
      *  `./Miniforge3-MacOSX-arm64.sh`
   * Then, to create your new environment, run the following commands:
      *  `conda config --set auto_activate_base false`
      *  `conda create --name coding3 python=3.9`
      *  `conda activate coding3`
      *  `conda install -c apple tensorflow-deps`
      *  `pip install tensorflow-macos`
      *  `pip install tensorflow-metal`
      *  `conda install -c conda-forge -y pandas jupyter`
      *  `python -m ipykernel install --user --name coding3`
* If you're not on an M1 or M2, go to the [miniconda downloads page](https://docs.conda.io/en/latest/miniconda.html) and get the Python 3.9 installer for Miniconda3 macOS Intel x86 64-bit pkg. Run the installer.

#### Windows or Linux users

Go to the [miniconda downloads page](https://docs.conda.io/en/latest/miniconda.html) and downoad the Python 3.9 installer for your machine (probably Miniconda3 Windows 64-bit). Run the installer.

### c. Check Your Installation 

Close any open Terminals or Command Prompts, then **reopen** a new one. 

#### Mac or Linux users

* ``which conda`` should return a message that doesn't look at all like "conda not found"
* ``which python`` should return a file path to a miniconda or miniforge installation 

#### Windows users

* ``where conda`` should return a message that doesn't look at all like "conda not found
* ``where python`` should return a file path to a miniconda installation
* 
#### Windows users - if you already have Python installed or the commands above show incorrect values

From the Start Menu, go to Control Panel => System and Security => System => Advanced system settings => Environment variables
(or just search 'Environment variables' in the Control Panel).

Make sure the path to the directory where Anaconda is installed is added to the "Path" variable.

If you have another version of Python installed, make sure the default path to Python is correct. You may change the default one or create a new one for the Anaconda Python. After adding/editing environment variables, close all cmd windows, open a new one and check ``where conda`` and ``where python`` again.

## 2. Set up an environment

A conda environment is a set of packages that you want to use together, along with a particular version of Python. You can have more than one environment installed, for instance if you want to make multiple projects that use different versions of libraries. [You can read more about environments here.](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/environments.html#:~:text=A%20conda%20environment%20is%20a,NumPy%201.6%20for%20legacy%20testing.) 

#### Mac M1/M2 users 
Skip this step, you did it already! (When you ran the terminal command `conda create --name coding3 python=3.9` above, you created an environment named `coding3`. You then installed jupyter and pandas libraries in this environment. Skip to Step 3 below.

#### Everyone else

Open up the terminal or console and type the following command:

``conda create --name coding3 python=3.9`` 

This will create a Python 3.9 environment named "coding3" (you can choose some other memorable name if you'd like)

Now run the following command to "activate" this environment (i.e., use it within this terminal/console session):

``conda activate coding3``

Next run the following command to install TensorFlow within the new enviornment:

``python -m pip install tensorflow``

Now, we'll install jupyter and pandas (two very useful tools) into this environment by running the following command:

``conda install -c conda-forge -y pandas jupyter``

**Make sure you are always using this environment when you do Python code for this unit, by running `conda activate coding3` at the beginning of any new session**

Finally, run:

``python -m ipykernel install --user --name coding3``

## 3. Test out your installation by launching Jupyter notebook

To test out the installation of your installation do the following:
1. Open a new terminal/console window. 
2. Activate your environment by running `conda activate coding3`
3. Launch a new Jupyter Notebook session (i.e., a browser-based session where you can do interactive Python coding) by typing `jupyter-notebook`. This should open a new browser window/tab with an orange logo and the word "Jupyter" at the top. 
4. Then click on the "New" button at the top right to make a new Python 3 notebook. You should see this new notebook open in a new browser tab, with a textbox that you can type into. 
<img width="836" alt="create_jupyter_notebook" src="https://git.arts.ac.uk/storage/user/226/files/72ef6a60-61ad-4c25-8497-45715517e6c7">
5. Type print("hi") into this textbox and then hold SHIFT while you press enter/return. You should see the word "hi" printed out for you.
<img width="793" alt="successful_python_print" src="https://git.arts.ac.uk/storage/user/226/files/55563f32-8fb2-48d8-8b5f-3a3d2132058b">
6. Create a new cell by pressing the [+] button in the top left corner
<img width="831" alt="create_cell" src="https://git.arts.ac.uk/storage/user/226/files/3ee96e37-e63a-44fc-9cc3-b47a1bfd7763">
7. In the new cell, type the following and then run it.

```python
import tensorflow as tf
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
```

If you successfuly print the number of GPUs like the example below, then your tensorflow is fully up and running! Congrats! (Note that if you have no GPU on your machine, this will say 0, and that's OK too.)
<img width="916" alt="print_gpus" src="https://git.arts.ac.uk/storage/user/226/files/a60c153b-b421-4488-a59f-62de66b76386">

## 4. Running code in the future

Every time you run Python, you will need to just do the following.

First, activate your environment:

`conda activate coding3`

Then, optionally, navigate to the directory on your machine where your code lives, e.g.:

`cd /Users/rebecca/coding3/`

Then, launch jupyter notebook:

`jupyter-notebook`

Don't forget to **leave your terminal window open for the duration of your Notebook session!**


## If you have problems

* First, tell Jasper, Adam, and/or Rebecca ASAP (on Slack) and get help. 
* If you make a mistake and want to start over you can deactivate your conda environment, delete it, and start from scratch:

```
conda deactivate
conda env remove -n coding3
```
* M1/M2 Mac users **only**: if you are unable to import and run tensorflow in a Jupyter notebook, you may need to use an older version of the software. To do this, first delete the current enviornment to start fresh:
```
conda deactivate
conda env remove -n coding3
conda create --name coding3 python=3.9
```

Then reinstall tensorflow using the following commands:
```
conda install -c apple tensorflow-deps==2.9.0
python -m pip install tensorflow-macos==2.9.0
python -m pip install tensorflow-metal==0.5.0
conda install -c conda-forge -y pandas jupyter
```

Now return to step 3 to test out your installation and see if you can import and run Tensorflow.

* At least one student has found [this youtube tutorial](https://www.youtube.com/watch?v=o4-bI_iZKPA) helpful for running on M1/M2

* In the very worst case, you can run your code on colab. [Read more about using colab at CCI here](https://git.arts.ac.uk/lmccallum/nlp-22-23/blob/main/Google-Colab.md). 

#### Windows users - if you keep having problems with Anaconda - alternative installation

* If you keep running into problems with Anaconda, you may want to create a 'regular' Python environment.
* Install Python 3.9 (https://www.python.org/downloads/) and pip (https://pip.pypa.io/en/stable/installation/)

    If you have another version of Python installed, you may want to create a new environment variable for it, like "python39" - instructions above.
* Open cmd
* Go to the directory where you want to create the virtual environment, e.g.:
  ``cd C:/coding_projects/cci-ual/cci-ual-coding-two``
* Create a new virtual environment:

``python -m venv coding-two-venv``

* Activate the virtual environment, e.g.:

``coding-two-venv\Scripts\activate.bat``

* Install pandas and jupyter:

``pip install pandas``

``pip install jupyter``

* check the Jupyter installation by running:

``jupyter-notebook``

* You may want to keep the paths and commands for running your virtual environment in a file on your Desktop and simply copy-paste them :)
