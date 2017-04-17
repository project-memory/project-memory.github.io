---
title: Environment Setup
layout: post
permalink: /environment-setup/
source-id: 1xxzBKH0Xsz0cdo8aWTvHNlrzrnxzoac63V6qLZJ_rqE
published: true
---
# Goals

* We should have a [Github repo](https://github.com/no-fire/line-follower)

* Each person should be able to...

* Run the code from last project on their laptop

* Access DeepThought and/or Nathan's Desktop and run intensive network training code

* Access and contribute to the training data repository 

# Instructions

## Things to install

* Python 2.7

    * Test: in terminal, run `python --version`

* ROS Kinetic

    * Test by running `rosversion -d` in a terminal

* ML Libraries:

    * [TensorFlow](https://www.tensorflow.org/install/)

        * Don't try to set up GPU support, it will end in fire and pain.

        * `sudo -H pip install tensorflow`

        * Test: in terminal, run `python -c "import tensorflow; print('Works!')"`

    * [Keras](https://keras.io/#installation)

        * `sudo -H pip install keras`

        * Test: in terminal, run `python -c "import keras"` It should say "Using TensorFlow backend."

* Misc

    * [Bcolz](http://bcolz.readthedocs.io/en/latest/install.html)

        * Test: run `python -c "import bcolz; bcolz.test()"`

    * [Numpy](https://scipy.org/install.html): The preferred way to run numeric computations in python. All hail Numpy.

        * Test: run `python -c "import numpy as np; np.test()"`

    * [Glob](https://pypi.python.org/pypi/glob2): Returns names of items in a directory as a list.

        * Test: run `python -c "from glob import glob; print('Works')"`

    * PIL

    * [Matplotlib](https://matplotlib.org/users/installing.html): Plots in python, based off of MatLab's plotting commands

        * `sudo apt-get install python-matplotlib` for Ubuntu Linux

        * Test: run `python -c "import matplotlib.pyplot as plt; print('Works!')"`

    * [Seaborn](http://seaborn.pydata.org/installing.html): Prettier plots on top of matplotlib

        * Test: `python -c "import seaborn as sns;print('Works')"`

    * [Tqdm](https://pypi.python.org/pypi/tqdm#installation): Adds progress bars to loops

        * Test: `python -c "import tqdm; print('Works')"`

## Working on a remote computer:

### Notes

* The examples here assume the remote computer is called 'nathanDesktop', the username is ‘nathan’, and DNS resolving works properly on your network.

* There is probably a better way to do this than using a shared user account. This is the solution

### Steps:

1. Get access to the remote computer using SSH public keys (once)

    1. Generate them ([Ubuntu Guide](https://help.ubuntu.com/community/SSH/OpenSSH/Keys))

    2. Transmit them to the owner 

        1. Your public key is found at `~/.ssh/id_rsa.pub`

        2. Send the contents of that file over email, Google Docs, etc.

        3. While you're at it, you should [add your SSH key to Github](https://github.com/settings/keys), if you haven’t already. It’ll allow you to access your repos without entering your u/n and password every time.

    3. Owner adds the keys to server

        4. All public keys should be stored in .ssh/authorized_keys 

        5. http://stackoverflow.com/questions/12392598/how-to-add-rsa-key-to-authorized-keys-file

2. Once remote owner authorizes access...

    4. Connect to the computer via ssh

        1. `ssh nathan@nathanDesktop`

    1. Open a terminal. If you are ssh-ing in, you'll already be in a terminal, but if you want to use tmux or another terminal, then:

        2. `tmux ls`

            1. Should print out that jupyter_server is running.

        3. `tmux a -t jupyter_server`

            2. Navigate tmux using ctrl+b, arrow key

            3. [https://learnxinyminutes.com/docs/tmux/](https://learnxinyminutes.com/docs/tmux/)

            4. [https://danielmiessler.com/study/tmux/#gs.=j=4xnE](https://danielmiessler.com/study/tmux/#gs.=j=4xnE)

    2. Open the remote jupyter server in your browser to start editing files

        4. `$ ssh -N -f -L localhost:8890:localhost:8890 nathan@nathanDesktop`

        5. Go to `localhost:8890/tree` in browser

        6. On Jupyter's Change kernel to 'Python [condaenv:deepLearning]’

    3. Want a file explorer - nautilus

        7. sftp://nathan@nathandesktop/home/nathan/olin/spring2017/line-follower

    4. Try broadcasting a message: `wall _____` 

## Code to download

Clone our repository into 
