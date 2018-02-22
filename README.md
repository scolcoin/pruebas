
Scolcoin development tree

Scolcoin is a PoS-based cryptocurrency.

Development process
===========================

Developers work in their own trees, then submit pull requests when
they think their feature or bug fix is ready.

The patch will be accepted if there is broad consensus that it is a
good thing.  Developers should expect to rework and resubmit patches
if they don't match the project's coding conventions (see coding.txt)
or are controversial.

The master branch is regularly built and tested, but is not guaranteed
to be completely stable. Tags are regularly created to indicate new
stable release versions of Scolcoin.

Feature branches are created when there are major new features being
worked on by several people.

From time to time a pull request will become outdated. If this occurs, and
the pull is no longer automatically mergeable; a comment on the pull will
be used to issue a warning of closure. The pull will be closed 15 days
after the warning if action is not taken by the author. Pull requests closed
in this manner will have their corresponding issue labeled 'stagnant'.

Issues with no commits will be given a similar warning, and closed after
15 days from their last activity. Issues closed in this manner will be 
labeled 'stale'.

Instructions install Deamon
----------------------------

### Step 1. Create a user for running scolcoind
This step is optional, but for better security and resource separation I
suggest you create a separate user just for running `scolcoind` .
We will also use the `~/bin` directory to keep locally installed files
(others might want to use `/usr/local/bin` instead). We will download source
code files to the `~/src` directory.

    $ sudo adduser scolcoin --disabled-password
    $ sudo apt-get install git
    $ sudo su - scolcoin
    $ mkdir ~/bin ~/src
    $ echo $PATH

If you don't see `/home/scolcoin/bin` in the output, you should add this line
to your `.bashrc`, `.profile`, or `.bash_profile`, then logout and relogin:

    PATH="$HOME/bin:$PATH"
    $ exit

### Step 2. Download scolcoind

We currently recommend scolcoind stable.

If you prefer to compile scolcoind, here are some pointers for Ubuntu:

    $ sudo apt-get install build-essential libssl-dev libdb-dev libdb++-dev libboost-all-dev git libssl1.0.0-dbg
    $ sudo apt-get install libdb-dev libdb++-dev libboost-all-dev libminiupnpc-dev libminiupnpc-dev libevent-dev libcrypto++-dev libgmp3-dev
    $ sudo su - scolcoin
    $ cd ~/src && git clone https://github.com/scolcoin/scolcoin.git
    $ cd scolcoin/src
    $ make -f makefile.unix RELEASE=1
    $ strip scolcoind
    $ cp -a scolcoind ~/bin
    
    ### Step 3. Configure and start icolcoind

In order to "talk" to `scolcoind`, we need to set up an RPC
username and password for `scolcoind`. We will then start `scolcoind` and
wait for it to complete downloading the blockchain.

    $ mkdir ~/.scolcoin
 
start `scolcoind`:

    $ scolcoind

