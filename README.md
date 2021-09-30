## See this tutorial online:
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/AkravasTheWise/Intro-to-magnetism-in-python/HEAD?filepath=binder_tutorial%2FREADME.ipynb)

# Intro to magnetism in Python
In the myriad of open source and academic code alternatives have risen because of the eagerness and need of the international student public for easy-to-use-and access tools. Being open source at inception, Python is an extraordinary language to code and automate tasks in. The purpose of this repository is not to give a complete bottom-up guide to scientific coding with Python since there are so many other good ones, but rather an introduction to data science and simulation in that language with actionable and easy to replicate examples that can be used at any level of proeficency. Think of this as a whitepaper to give the reader a taste of the many advantages of using Python for computational magnetism.

This tutorial is intended for members of the [Applied Spintronics Group](http://www.akermanlab.com/) at the University of Gothenburg, but anyone is free to use it and report feedback on it. Also, if you know any tools that I might want to include in my toolbox, please let me know.

## Installing and environments: the quick-and-dirty

As any other programming language, Python works by importing prevously written code for particular tasks. What diffentiates it from other languages is that most the most powerful codes for data science and science applications is open source and has a great and supportive community that is happy to help for free. A previously written code that provides ready-to-use functions and features is called a **module**. A collection of modules designed for a particular functionality (for example plotting, image analysis or matrix operations) is called a **package**. 

In order to get and work with packages, we must use programs called package managers. The most popular ones are called **pip** and **Anaconda**. Pip is a very flexible manager designed for the [Python Package Index](https://pypi.org/) (PyPI), the largest package repository. If you highly value versatility, pip might be worth the effort to master for the abundance of experimental and cutting-edge code that you can toy with in PyPI. Anaconda, on the other hand, is a package manager designed for data science specifically. So, it is more streamlined but somewhat less versatile. Personally, I have both in my toolbox and I switch between them depending from the task at hand. 

It's worth saying that it doesn't matter if you install a package with Anaconda or pip, it'll be used in the same way in your particular script. Now that we're familiar with some of the terminology, we can jump into installing Python.

### Getting Python

If you have a **Linux** based machine, congrutations, you most likely already have Python. Check the version of Python you have by typing this in your preferred terminal:

`$ python -V`

If you have a 3.6 or older version of Python, you might want to consider updating it to 3.8 or newer, since those older versions are currently [not being supported or won't be supported soon](https://www.python.org/downloads/) and will become obsolete. To install python 3.8, just type:

`$ sudo apt-get update`
    
`$ sudo apt-get install python3.8 `

Now, you can use the command `python3` for running python codes, opening text editors and more advanced operations we'll see later like administering packages and accesing virtual environments. Depending on your OS, `python` might also work, but in debian-based distributions like Ubuntu this is legacy for Python 2.x, so feel free to experiment on your own. If you also want a streamlined Python package manager in Linux, I also recommend checking out Anaconda in the link below.

For **Windows** based machines, I highly recommend Anaconda, as it comes included with Python and pip and a ton of other features and an intuitive command line that it's very similar to the very popular Linux syntax. You can [download Anaconda from their website](https://www.anaconda.com/products/individual) and just run the executable as you would with any other program. The Anaconda version of PyPI is the Conda Forge. To open the *Anaconda Prompt* (or terminal) just hit the windows key, type 'Anaconda' and click it. This terminal will be out operation hub for installing packages, running scripts and activating virtual environments.

If you want to explore your options, you can also download your preferred Windows relase from the [Python website](https://www.python.org/downloads/) and set it up on your own. Fair warning that the standard Windows command line is not very flexible for this purpose and you might want to download and install the [Windows PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1) in order to have an environment to work with.

So, how about pip? Well, `pip` already comes included with both Python 3 >= 3.4 and Anaconda, so we should be fine with either of the options you chose above. You can even use `pip install` with Anaconda! If you want to personalize your setup, [check the pip documentation](https://pip.pypa.io/en/latest/installing/).

### Virtual environments

Alright, so we have our package manager(s) up and our Python release up and running. Let's take a minute to discuss compatibility issues that may arise from package diversity. Let's say you have updated to a new version of your favorite package `miracleSolver.py` and soon found that the modules of this new update have different names or additional features and your old codes are suddenly broken. One thing you could do would be to painstakingly update your scripts one by one to the new release or just revert to the old one and miss out on those sleek new features. Since there is no good option among those two, I recommend that you use virtual environments.

A virtual environment is like a fresh separate installation of Python that we can tinker around with. Nothing we do or install in the virtual environment will affect our general Python environment and viceversa. Even more, you can specify the Python release you want to use, further customizing your compatibility capabilities. The package that creates virtual environments can be called using the `venv` command and it it nominally included in . To create a new environment in **Anaconda**, type:

`$ conda create --name myShinyNewEnvironment `

It will prompt you to confirm the creation of the environment and its path. `myShinyNewEnvironment` will be created in the `envs` folder within the `Anaconda3` directory you picked at installation. Just type `y` when prompted with `proceed ([y]/n)?` and hit enter. 
    
To activate the environment, simply type:

`conda activate myShinyNewEnvironment`
    
You will see that the words in parentheses have changed from `base` to `myShinyNewEnvironment`
    
![Change of command line in the new environment](images/newenv_Anaconda.png)

Those parentheses mean that you're no longer on your base Python release, but rather in a virtual one and anything you do here won't break things outside. To specify the python version you want to use in a given environment, type:
    
`conda -n anotherEnv python=3.6`
    
If you want to create an environment and install a package (`myNeatPackage`) on it:
    
`conda -n anotherEnv myNeatPackage`
    
Feel free to get creative with whatever you need. If you went the condaless route, with **pip** only, then you must use:

`python -m venv a\useful\path\myShinyNewEnvironment`
   
Replacing `a\useful\path` with whichever path you want to use. Consider that any virtual environment you create this way can be activated using conda and viceversa if saved in `Anaconda3\envs`. To activate the environment in Windows PowerShell:

`myShinyNewEnvironment\Scripts\activate.bat`

For the Linux terminal:

`source myShinyNewEnvironment/bin/activate`

As you can tell, Anaconda takes care of most of the heavy lifting and it makes your life easier when handling environments by not having to worry which OS you're in. 
    
As a general rule, you want to create an environment for each different coding project you take on. That way, if you copy the project and clone its environment, you can use any other machine and get consistent results. If you want to more about virtual environments in [Anaconda you can check here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) or [click here for a more general (condaless) use of them](https://docs.python.org/3/library/venv.html).
    
To finish, we'll visualize some randomly generated points in just a line as a practical example. First off, create a environment, I'll call it `testEnv`:
    
`conda create -n testEnv python=3.8 scipy matplotlib -y`
    
With just that line, we are creating a new virtual environment in Python 3.8 and installed the `scipy` (Scientific Python) and `matplotlib` (useful and quick plotting) packages. Go to the environment:
    
`conda activate testEnv`
    
And now we plot some randomly generated data:
    
`python -c "import numpy as np; import matplotlib.pyplot as plt; plt.plot(np.linspace(0,2*np.pi,100), np.sin(np.linspace(0,2*np.pi,100)) + np.random.rand(100)); plt.show()"`
    
Which is just a sine function with some random noise thrown in. I have used some tools that will be explained later, but the gist is there. Just importing the `numpy` and `maptlolib` packages, we gain so much that I could probably write another thousand words about them. This tutorial is long enough, so we'll leave it here.
    
Feel free to explore the tutorials according to your interests after you are done with the three-part introduction. And guess what? You are done with part one.
    
[**Part 2: Scripts, functions and the Jupyter Notebook**](ScriptsJupyter.md)
