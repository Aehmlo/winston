# Installation

Someday I'll make this easy, but for now, it's slightly annoying.

## OpenBCI

The current OpenBCI submodule is for a Python library that shouldn't require anything other than Python 2.7 and NumPy 1.7. See [`openvibe/README.md`](openvibe/README.md) for more information.

From the NumPy website:

```shell
sudo apt-get install python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose
```

## OpenViBE

We have to actually build OpenViBE. To do this, we first have to install some dependencies. They provide a script that can do this for us (though we'll eventually want to improve upon this, because it's…not great). It must be run from within the `openvibe/scripts` directory, for some reason. The only dependency listed for the script is GCC 4, although I'm skeptical of that.<sup>1</sup>

This will, of course, require root permissions.

```shell
cd openvibe/scripts
./linux-install_dependencies
```

With the dependencies installed, we can build OpenViBE. I've done some of the grunt work for you, but due to some questionable decisions by the maintainers of OpenViBE involving large files, I can't host my forked OpenViBE repository on GitHub. Instead, I've prepared [a patch](0001-Make-suggested-modifications-to-config-files.patch) that can be applied to the OpenViBE submodule.

Let's apply the patch!

```shell
cd openvibe
git am ../0001-Make-suggested-modifications-to-config-files.patch
```

Now we can build the thing as normal.

```shell
cd openvibe/scripts
./linux-build
```

Et voilà! Assuming that succeeded, a local build of OpenViBE will be in `openvibe/dist`.

----

<sup>1</sup>All of the sample commands I give will assume you're running them from the root of the repository; alter the `cd` portions as needed if that's not the case.
