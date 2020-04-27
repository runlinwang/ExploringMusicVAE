# Setup

In this project, I had to install a number of new packages for the magenta package and the MusicVAE framework, which I've listed below for others to replicate. These instructions were adapted from the official Github of magenta, which is cited in the README.md document.

```sh
pip install magenta
pip install oauth2client==2.0.1
pip install gym==0.14.0
pip install httplib2==0.12.0

git clone https://github.com/tensorflow/magenta.git
cd magenta
pip install -e .
```
