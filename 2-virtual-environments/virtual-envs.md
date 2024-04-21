# Virtual Environments

A virtual environment is created on top of an existing Python installation, known as the virtual environment’s “base” Python, and may optionally be isolated from the packages in the base environment, so only those explicitly installed in the virtual environment are available.

It is quite important because it allows you to separate different package versions of the code. For example, if you are using `scikit-learn` in one experiment, save your model with that version (e.g. Python 3.7) and later try to open the file with a new version (e.g. Python 3.11), there may be problems when reading the file.

## Prerequisites

* An installed version of Python, it could be 3.7,..., 3.11

## Available options

You can use several options to create the virtual environments, some examples are:

* [venv](https://docs.python.org/3/library/venv.html)
* [conda](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
* [pyenv](https://github.com/pyenv/pyenv-virtualenv)

**In this tutorial, we will be using `venv`.**

## Creating virtual environments

Creation of virtual environments is done by executing the command venv:

```bash
python -m venv venv
```

Running this command creates the target directory (creating any parent directories that don’t exist already) and places a pyvenv.cfg file in it with a home key pointing to the Python installation from which the command was run (a common name for the target directory is `venv` or `.venv`).

![venv.png](https://github.com/carloslme/python-for-production-envs/blob/main/2-virtual-environments/images/venv.png?raw=true)


It also creates a `bin` (or Scripts on Windows) subdirectory containing a copy/symlink of the Python binary/binaries (as appropriate for the platform or arguments used at environment creation time). It also creates an (initially empty) `lib/pythonX.Y/site-packages` subdirectory (on Windows, this is `Lib\site-packages`). If an existing directory is specified, it will be re-used.

![venv1.png](https://github.com/carloslme/python-for-production-envs/blob/main/2-virtual-environments/images/venv1.png?raw=true)

### How to create a `venv` in Windows

* Create the `venv`

    ```bash
    python -m venv venv
    ```

* Activate the `venv`
    Once an environment has been created, you may wish to activate it, e.g. by sourcing an activate script in its bin directory.

    ```bash
    venv\Scripts\activate.ps1
    ```

    ![venv_activate.png](https://github.com/carloslme/python-for-production-envs/blob/main/2-virtual-environments/images/venv_activate.png?raw=true)

### How to create a `venv` in MacOS

* `cd` to your project directory and run `venv` to create the new virtual environment.

* The following commands will create a new virtual environment under my-project/venv.

    ```bash
    cd my-project
    python -m venv venv
    ```

* Activate the `venv`
    Now that we have a virtual environment, we need to activate it.

    ```bash
    source venv/bin/activate
    ```

## Install libraries with `requirements.txt`

The `requirement.txt` file serve as a list of items to be installed by [`pip`](https://realpython.com/what-is-pip/). Files that use this format are often called `requirements.txt`, although, that is not a requirement. Check [this](https://pip.pypa.io/en/stable/reference/requirements-file-format/) out to learn more about it.

For this section, ensure you have activated the virtual environment, and create a `requirements.txt` file in the `2-virtual-environments/` directory, then, copy and paste the following code and save the file:

```bash
scikit-learn==1.2.2
```

Once the file is created, run the following command to install the required libraries within the virtual environment:

```bash
pip install -r 2-virtual-environments/requirements.txt
```

After the installation, verify it by running this command.

```bash
pip freeze
```

You should see something like this:

```bash
joblib==1.4.0
numpy==1.26.4
scikit-learn==1.2.2
scipy==1.13.0
threadpoolctl==3.4.0
```

(There may be some variation in the libraries depending on the version of 'Python')

## Run the script

Once you have activated your virtual environment and installed the requirements, just run the command as follows:

```bash
python 2-virtual-environments/svr.py  
```

You should see something like this:

```bash
The prediction is [1.5]
```

**Congrats!**  
You have run your first script using a virtual environment on a local computer.

## Deactivate the `venv`

To deactivate the virtual environment, you just need to run the following command:

```bash
deactivate
```

And you will have one more time access to the global environment.
