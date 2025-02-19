# the-crown-defcon615

<p align="center">
<img src="https://user-images.githubusercontent.com/57866415/149668922-0e0be26e-a174-4a2c-99e8-607d0cbe9883.png">
</p>

Repo for "The Crown: Exploratory Analysis of Nim Malware" DEF CON 615 talk

## Instructions
This entire talk is a series of Jupyter Notebooks!

To use this repo, you can do one of two things.

The Notebooks offer a guided walkthrough of Nim research, and you can simply read and interact with them entirely in Jupyter Notebooks. Think of it like an interactive museum exhibit or science fair project!

But if you want the most out of the material, you can set up a mini malware analysis workstation, examine the code, examine the binaries, all kinds of stuff! It's up to you. 

## 🐋 Oh Snap It's Dockerized? Docker Quickstart
For those of you who are down with the Whale:
```
$ git clone https://github.com/HuskyHacks/the-crown-defcon615.git && cd the-crown-defcon615
$ sudo docker build -t thecrown .
$ sudo docker run -t -p 8888:8888 -p 1738:1738 thecrown:latest
```
Then, copy and paste the URL into your browser.

## Install From Source
### If you want to do just the stuff in the notebooks...
- Clone this repo:
```
$ git clone https://github.com/HuskyHacks/the-crown-defcon615.git && cd the-crown-defcon615
```
- Install pip3 (if you don't already have it)

Example on Linux:
```
$ sudo apt-get install python3-pip
```
- Install `poetry` and add it to your path (rebooting after the pip install makes this way faster):
```
$ pip3 install poetry

[example for a user with a Bash shell]
$ echo "export PATH=$PATH:$HOME/.local/bin/" >> ~/.bashrc
$ source ~/.bashrc

(or, exit and open a new terminal)
```
- Enter a Poetry shell (must be in the main repo directory if not already):
```
$ poetry shell
```
- From the poetry shell, install all the project dependencies:
```
$ poetry install
```
- Start Jupyter Lab!
```
$ jupyter lab main.ipynb
```

### If you want to do everything that I do in the talk, including all of the malware analysis stuff...
You'll need to do the following:

- Install this repo by following the steps that are above this section.
- Install Nim using [choosenim](https://github.com/dom96/choosenim):
```
$ curl https://nim-lang.org/choosenim/init.sh -sSf | sh
```
- Set up a Windows analysis VM. I recommend [FLARE-VM](https://github.com/mandiant/flare-vm).
- Transfer the samples to your analysis VM and examine them with the tools that are noted in the presentation.

## Lab Safety
All **compiled binaries** available in this repo are designed to be completely harmless. Of the compiled binaries:
- One is a simple Hello World in Nim.
- Two spawn Notepad.exe by invoking the ShellExecute Win API (one is written in Nim, one in C++. Both are identical in terms of functionality).
- One is a simple echo server.

The source code for all compiled binaries is available in the `samples/src/` directory and you are free to inspect the code as you wish.

Also note that there is source code in that directory that has more weaponizable/dangerous functionality (i.e. `createremotethread.nim`). Though each of the samples are not fully weaponized (pops calc.exe instead of a Cobalt Strike beacon) I have not compiled any source that I've deemed unsafe for this presentation.

I'll leave it as an exercise for the reader to fully weaponize any of the source code in this repository for research purposes only.
