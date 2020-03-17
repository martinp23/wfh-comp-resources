- [Installing and using xtb](#installing-and-using-xtb)
  * [Install XTB](#install-xtb)
  * [Install jmol to visualize results](#install-jmol-to-visualize-results)
  * [Playing with xtb](#playing-with-xtb)
    + [Defining molecular structures](#defining-molecular-structures)
    + [What can you do with xtb?](#what-can-you-do-with-xtb-)
      - [Single point](#single-point)
      - [Optimization](#optimization)
      - [Hessian calculation](#hessian-calculation)
    + [Visualising results](#visualising-results)

## Installing and using xtb

### Install XTB

Pre-requisites: Be running a unix system or have Windows Subsystem for Linux installed with a suitable Linux distribution (this tutorial tested with ubuntu)

Download the latest _release_ version from here: [https://github.com/grimme-lab/xtb/releases/](https://github.com/grimme-lab/xtb/releases/) . Choose the xtb-[numbers].tar.xz file. At the time of writing, that is xtb 6.2.2, which has the filename xtb-191209.tar.xz.

Copy the xtb-191209.tar.xz file (or latest version) to wherever you want to install it; I recommend $HOME. For WSL, you can find this by navigating to \\\wsl$\Ubuntu\ in Windows explorer, then going through the directory tree: /home/ then your username.

Open a bash terminal (or your WSL distribution). Extract the archive containing xtb using: tar xf xtb-191209.tar.xz  (you can probably tab-complete to get the complete file path after you&#39;ve typed xtb).

Check that it works: `./xtb_6.2.2/bin/xtb`  should give output complaining that it has no geometry.

Let's make it easier, so you don't need to type the whole path every time you run xtb. Here we'll follow instructions from the manual to put relevant lines into your `.bashrc` file. [https://xtb-docs.readthedocs.io/en/latest/setup.html](https://xtb-docs.readthedocs.io/en/latest/setup.html)

- Open .bashrc for editing (e.g. using nano or vim, or notepad++ if you're in WSL)
- Paste the following lines into it (if you're using the WSL terminal emulator, pressing right click = paste), changing the path to the xtb directory in the first line as necessary:

```bash
XTBHOME=$HOME/xtb_6.2.2
# set up path for xtb, using the xtb directory and the users home directory
XTBPATH=${XTBHOME}/share/xtb:${XTBHOME}:${HOME}
# to include the documentation we include our man pages in the users manpath
MANPATH=${MANPATH}:${XTBHOME}/share/man
# finally we have to make the binaries and scripts accessable
PATH=${PATH}:${XTBHOME}/bin
LD\_LIBRARY\_PATH=${LD\_LIBRARY\_PATH}:${XTBHOME}/lib
PYTHONPATH=${PYTHONPATH}:${XTBHOME}/python
export PATH XTBPATH MANPATH LD\_LIBRARY\_PATH PYTHONPATH
```

- Read the new bashrc using source .bashrc
- Now type xtb. You should get the same error as before, without giving the full path to the executable.

### Install jmol to visualize results

First you will need to install Java. I'm sorry for the indignity this may cause.

Next get jmol from here: [http://jmol.sourceforge.net/download/](http://jmol.sourceforge.net/download/) and follow the instructions.

### Playing with xtb

The xtb manual contains a wealth of tutorial-style exercises, available here: [https://xtb-docs.readthedocs.io/en/latest/basics.html](https://xtb-docs.readthedocs.io/en/latest/basics.html). However, that website might be intimidating if you are a beginner. 

This short tutorial cannot hope to give you all the info you need about computational chemistry, but I will aim to get you up-and-running with some basic calculations.

The key ingredients for a calculation are

1. A molecular structure.
2. Some instructions about what the program should do with it.

Let's take each of those in turn. 

#### Defining molecular structures

xtb accepts two types of structure input: a `coord` file in the style of Turbomole, or an `xyz` file. This tutorial will use `xyz` files, which have the following format (with each line specified):

1. Number of atoms in the file
2. A comment line, can be blank but must be present
3. (to end) A list of atom positions, one atom per line, in the following format: ATOMTYPE XCOORD YCOORD ZCOORD

Notice that we don't need to specify bond orders. You can draw molecules and save them as xyz format using the free software [https://avogadro.cc/](Avogadro), or using the Chem3D part of the ChemOffice package. Note that from Chem3D you should save as Gaussian input (gjf extension) then copy the xyz coordinates from the file.

I have included an example xyz file for a distorted benzene below (as an attachment), as well as an xtb-optimized structure. Take a look at the structure of the file.

#### What can you do with xtb?

The manual is the best answer to this question! But you can get an overview of possible commands using the internal help command: `xtb -h`. The main calculations you are likely to use, at least initially, are _single point_, _geometry optimization_, and _hessian_ calculations.

##### Single point

If you run xtb with just an xyz file as an argument, the program will perform a _single point_ calculation. Let's try this with benzene, for which the xyz file can be found attached to this gist:

```
xtb benzene-begin.xyz
```

Now scroll through the output. 

First, a load of references are listed. If you publish results involving xtb, you should cite them. Then various parameters are listed: these control how the method is parameterized (i.e. how electrons behave in the model). Then more details of the system are printed in a box headed `SETUP`, followed by a short table of SCF iterations. 

After that, you get a table of orbital occupations and energies. This table is likely to be fairly meaningless, because I have provided a really terrible start geometry for benzene. Note that this benzene is substantially open-shell! 

Afterwards we get a summary of the electronic properties, including the HOMO-LUMO gap. Note that it's just 0.04 eV, which is ridiculous for a stable aromatic molecule. Clearly we need a better geometry! 


##### Optimization

So let's do a geometry optimization:

```
xtb benzene-begin.xyz -o
```

In this calculation, the single point procedure is repeated but then the atomic coordinates are changed with respect to the forces (i.e. the first derivative of the energy with respect to displacement) on the atoms. This process repeats until the forces or displacements are below certain tolerances, hopefully approaching a minimum in the energy (or at least a stationary point on the potential energy surface).

You'll be able to see this process if you read the calculation output. Notice at the end that we have a lower final energy, and a larger HOMO-LUMO gap (near 5 eV), which is more consistent with that for a stable molecule.

Note that the final geometry is saved to the xtbopt.xyz file. Your original `benzene-begin.xyz` is preserved in its distorted form.

##### Hessian calculation

A geometry optmization is good at finding a stationary point (i.e. where the gradient of energy with respect to displacement is nearly zero), but can fail to discriminate between a minimum and a maximum on the potential energy surface (i.e. a transition state). 

If you think back to high school(?) maths, you'll remember that the way we find the sign of a stationary point is by finding the second derivative at that point. That's what the Hessian is: the second derivative of the energy with respect to displacement.

At a minimum, all the values in the Hessian are positive. At a transition state or higher-order stationary point, then one or more values are negative (also known as 'imaginary'). The results from a Hessian calculation are presented as vibrational frequencies with units of cm^{-1}.

```
xtb xtbopt.xyz -hess
```

Look through the output and you'll find projected vibrational frequencies and intensities. Crucially, there are no substantial negative values. Note that there should always be 6 values near zero: these correspond to translational and rotational modes.

For the sake of illustration, let's see what the output of this calculation looks like for our terrible starting geometry

```
xtb benzene-begin.xyz -hess 
```

Two things to note: first we have four negative frequencies, which might indicate that we're at a very high-order stationary point (i.e. a maxmimum in 4 dimensions). But there's also an error: `- Hessian on incompletely optimized geometry!` The gradient (of energy with respect to displacement) is not zero at this geometry, so it's not a stationary point. Therefore interpretation of the Hessian as though it describes a stationary point is invalid.

One final note in this section: you can do a combined optimization and Hessian calculation:

```
xtb benzene-begin.xyz -ohess
```

Now you will have zero imaginary frequencies.


#### Visualising results

So far we haven't actually seen a structure!

You can open xyz files in jmol for visualization. Alternatively you can open them in a program like [Chimera](https://www.cgl.ucsf.edu/chimera/download.html) or [molden](http://cheminf.cmbi.ru.nl/molden/) [direct download link for Molden 6.2 for Ubuntu](ftp://ftp.cmbi.umcn.nl/pub/molgraph/molden/bin/Linux/molden6.2.full.ubuntu.64.tar.gz).

You can get more information for viewing in jmol or molden by running xtb with an extra flag:

```
xtb xtbopt.xyz -molden 
```

A file called `molden.input` is printed, which can be opened in jmol or molden. You can use this file to visualise vibrational frequencies, "orbitals" and other molecular surfaces, and structures. 

For WSL users:

* *jmol*: first copy the molden.input file to your local filespace (e.g. using Windows explorer as described above). Then open it in jmol.
* *molden*: it's best to install molden (by downloading and extracting it) into WSL. You will need to install some pre-requisite packages (at least `sudo apt install libgfortran3`). You can then run molden from within WSL, `molden molden.input`.

