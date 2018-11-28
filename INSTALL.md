# Installation

Someday I'll make this easy, but for now, it's slightly annoying.

## OpenBCI

The current OpenBCI submodule is for a Python library that shouldn't require anything other than Python 2.7 and NumPy 1.7. See [`openvibe/README.md`](openvibe/README.md) for more information.

From the NumPy website:

```shell
sudo apt-get install python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose
```

## OpenViBE

We have to actually build OpenViBE. To do this, we first have to install some dependencies. They provide a script that can do this for us (though we'll eventually want to improve upon this, because it's…not great). It must be run from within the `openvibe/scripts` directory, for some reason. The only dependency listed for the script is GCC 4, although I'm skeptical of that.

This will, of course, require root permissions.

```shell
cd openvibe/scripts
./linux-install_dependencies
```

With the dependencies installed, we can build OpenViBE.

```shell
cd openvibe/scripts
./linux-build
```

Et voilà! Assuming that succeeded, a local build of OpenViBE will be in `openvibe/dist`.
