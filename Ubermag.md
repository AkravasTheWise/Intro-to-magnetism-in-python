# Intro to Magnetism in Python, part 3

## Micromagnetics simulations with Ubermag

So far, you have seen the bare bones of what you need to install, write and run Python sripts and notebooks. Although I gave an example with data fitting on part 2, at the beginning
I said that I wanted magnetic-specific instances that we can apply to our work or even tinker around with for whatever purpose. This closing tutorial is one of those instances. 

[**Ubermag**](https://ubermag.github.io/) is a recent project by Marijan Beg, Hans Fangohr and collaborators that adds another layer of abstraction on top of the existing two most 
popular micromagnetics (mms) simulation programs (or calculators): [OOMMF](https://math.nist.gov/oommf/) and [mumax&#179;](https://mumax.github.io/). It acts as a user frontend for 
the mms calculators and they can be selected indistinguishably within the same workflow. Therefore, not only can we save the opening of a new instance of a certain calculator, but 
we also have a common language between calculators so the simulation cells, mesh and parameters do not need to be translated from one to the other when comparing approaches. 
Furthermore, it allows for other options like the simulation to take place inside [Docker](https://www.docker.com/) container, for easy portability; and to perform a computation 
online for free in the nanoHUB cloud via [Binder](https://ubermag.readthedocs.io/en/latest/ipynb/ubermag-cloud.html). 

There is a good guide as well as a deep-dive tutorial series from Beg on the [IEEE Magnetics website](https://www.spintalks.org/tutorials) that is worth checking out after you are
done with this part. This final tutorial has been inspired from the Ubermag documentation and I will keep things short for the sake of brevity, but you should definetely take a look
into his videos as he goes into detail about the basics of mms and the different aspects of the Ubermag package. The recommended method for installing Ubermag, by its developers, is
using **Anaconda**. Open up a terminal, create, and activate an environment, I'll call it `ubermag` for simplicity:

```
conda create -n ubermag python=3.8 -y
conda activate ubermag
```

My use of the `-y` flag is to avoid the confirmation prompt that comes out when you are making changes to Python, but you can do without in this and the next commands if you'd like 
to review the different packages you'll be installing. Once again, the Ubermag meta package requires specific updated versions of many common Python packages, and we create and enter
the virtual environment so we don't break anything outside it during installation. Same will be true when you want to use Ubermag, you'll have to activate it. Once inside, we will
install it with:

```
conda install --channel conda-forge ubermag -y
```

Simple as that. To test the installation, type:

```
python -c "import ubermag; ubermag.test()"
```

If no errors show up, the installation has been sucessful. Otherwise, delete the environment and try it again. IF you have decided not to use Anaconda, there is also a manual
installation of the individual components. Neither I or the developers recommend this approach, but it can be found under 
[Advanced installation at the Ubermag docs website](https://ubermag.readthedocs.io/en/latest/ipynb/advanced-installation.html). Once with that, we can start exploring and simulating
mms systems with either calculator. 

Below, I have prepared a notebook with descriptive examples of magnetic vortices in a disk and a domain wall pair conversion. You can just check out the notebook, but Gitlab is not adequate
for this. Preferably, you can download it and run it locally within your newly-minted virtual environment. 

[Ubermag notebook: quick demonstration of vortex dynamics](SkyrmionUbermagExamples.ipynb)

Now, you should have the basic tools to start using the Jupyter Notebook environment for Python prototyping and mms simulations. As the repository gets populated, more sample 
scripts and notebooks will become available so you can download and use. Please feel free to make requests either here or at the group's wiki. Thank you for making it this far
and I hope to write more tutorials soon.

*Victor H. González*