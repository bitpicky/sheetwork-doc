# Installation & Update

## Get sheetwork

{% hint style="info" %}
**Python 3.6 and up**

sheetwork is written in python and is compatible with versions of python 3.6 and up. Make sure you get that sorted before you get started with sheetwork.

Our developers are currently using Python 3.7.
{% endhint %}

### Using \`pipx\` \(Strongly Recommended\)

`pipx` is a really cool way to install applications globally \(kind of like brew\) although under the hood the application will reside in its own virtual environment which prevent from some issues with packages that conflict each other --which would be the case if you installed `sheetwork` via `pip` globally.

1. install pipx via brew: `brew install pipx`
2. once installed you can now use pipx to install sheetwork. 

```bash
pipx install sheetwork
sheetwork --version
```

if `sheetwork --version` ran and printed a version in your terminal you're good to go!

### Using pip & venv \(or any of your preferred virtual env management tool\)

If you prefer to create a special virtual environment for sheetwork, the following method is also a safe way to install and use sheetwork

1. **sheetwork** is distributed via [Python Index PyPi](https://pypi.org/project/sheetwork/)
2. we recommend that you set up and run sheetwork from a **virtual environment** to keep things clean, to avoid package requirements collisions and other nasties. Here's a fantastic [resource from Real Python on how to set up virtual environments](https://realpython.com/python-virtual-environments-a-primer/).
3. activate your virtual environment and the following command should take care of the rest:

```bash
pip install sheetwork
sheetwork --version
```

if the `--version` command printed a sheetwork version in your terminal you're good.

## Update sheetwork

### Using pipx

If you have installed `sheetwork` using [`pipx`](https://github.com/pipxproject/pipx) you can update your app from anywhere. Open a terminal window and run the following command:

```bash
pipx upgrade sheetwork
```

### Using pip & venv

If you have set up `sheetwork` inside a specific virtual environment you'll need to fo the following:

1. activate your virtual environment
2. run `pip install -U sheetwork` 

