obscuraX Core version 0.12.3
===============================

`master:` [![Build Status](https://travis-ci.org/obscuraxpay/obscurax.svg?branch=master)](https://travis-ci.org/obscuraxpay/obscurax) `develop:` [![Build Status](https://travis-ci.org/obscuraxpay/obscurax.svg?branch=develop)](https://travis-ci.org/obscuraxpay/obscurax/branches)

https://www.obscurax.com


What is obscuraX?
----------------

obscuraX is an untraceable x11 token that is Secured by nodes hidden behind the .onion (TOR) routing system. ObscuraX is TOR compatible featuring dedicated nodes that facilitate instant confirmation payments, private sending, masternode reward systems, and Multiple party transaction mixing. obscuraX Core is the name of the open
source software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the obscuraX Core software, see https://www.obscurax.com/.


License
-------

obscuraX Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is meant to be stable. Development is normally done in separate branches.
[Tags](https://github.com/obscuraxpay/obscurax/tags) are created to indicate new official,
stable release versions of obscuraX Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.
<BR>
<BR>
<BR>
<

***Masternode Setup Guide***


***---GUI WALLET---***

1. Open your wallet and wait until the wallet has fully synced.

2. Go to “Tools”. 
Click “Debug console”. 

3. Create a masternode private key by typing the following:
masternode genkey

Example output:
75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo

4. Show your collateral address by typing the following:
getaccountaddress "MN1"

Example output:
Nad4xtgdwf7c5y45ruy5MWtVY43zYMCvva

*******Keep note of the masternode private key and the collateral address.********




***---VPS SERVER---***
Install Ubuntu Server 18.04 on a VPS.

Update your Ubuntu machine.

5. sudo apt-get update
6. sudo apt-get upgrade

Install the required dependencies.

7. sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev
8. sudo apt-get install libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common




Install Berkeley DB.

9. sudo add-apt-repository ppa:bitcoin/bitcoin (Hit Enter on prompt)<BR>
10.sudo apt-get update<BR>
11.sudo apt-get install libdb4.8-dev libdb4.8++-dev<BR>

DOWNLOAD THE DAEMON AND WALLET<BR>
12.wget "https://github.com/obscuraxofficial/Linux-Daemon/blob/master/obscurax-daemon-linux.tar.gz?raw=true" -O obscurax-daemon-linux.tar.gz<BR>
13.wget "https://github.com/obscuraxofficial/Linux-wallet/blob/master/obscurax-qt-linux.tar.gz?raw=true" -O obscurax-qt-linux.tar.gz<BR>



EXTRACT TAR FILES<BR>
14.tar -xzvf obscurax-daemon-linux.tar.gz<BR>
15.tar -xzvf obscurax-qt-linux.tar.gz<BR>


INSTALL THE DAEMON AND WALLET<BR>
16.sudo mv obscuraxd obscurax-cli obscurax-tx /usr/bin/<BR>


CREATE CONFIG FILES<BR>
17.mkdir $HOME/.obscurax<BR>
18. Enter the following command and paste or type the below config <BR>

***BE SURE TO REPLACE THE 2 LINES NOTED BELOW.***

$ nano $HOME/.obscurax/obscurax.conf


#----
rpcuser=rpc_obscurax
rpcpassword=kuw05sqio7bcm8z96o7redv17xws1lw6xpd1qf33
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
port=5112
maxconnections=64
#----
masternode=1
masternodeprivkey=REPLACE_WITH_MASTERNODE_PRIVATE_KEY
externalip=REPLACE_WITH_EXTERNAL_IP_OF_VPS
#----



***Replace the text “REPLACE_WITH_MASTERNODE_PRIVATE_KEY” with the “masternode private key” that you created using the command “masternode genkey”.***
E.G. masternodeprivkey=75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo

***Replace the text “REPLACE_WITH_EXTERNAL_IP_OF_VPS” with the external IP address of your VPS.***
E.G. externalip=116.194.571.221


19. CTRL+o TO SAVE
20. CTRL+X to exit back to command

START NODE<BR>
21. obscuraxd



***MASTERNODE ACTIVATION***<BR>
22.Send EXACTLY 10,000 OBSX to the “collateral address” that you created using the command “getaccountaddress MN1
***Wait for AT LEAST 15 confirmations***






***---GUI WALLET---***
23. Go to Tools. 
24. Click Debug console.

25. Enter the following command:
masternode outputs

Example output
{ "06e38868bb8f9958e34d5155437d009b72dff33fc28874c87fd42e51c0f74fdb" : "0", } 

26. Go to “Tools”. 
Click “Open Masternode Configuration File”. (if it asks what program to use choose "notepad")

27. Modify the following line in  notepad using the information saved from the commands issued earlier.

MN1 136.144.171.201:5112 75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo 06e38868bb8f9958e34d5155437d009b72dff33fc28874c87fd42e51c0f74fdb 0

MN1 - Alias for your masternode.<BR>
136.144.171.201 - External IP of your VPS.<BR>
5112 - P2P port. (leave this as is)<BR>
75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo - Masternode private key from the command “masternode genkey”.<BR>
06e38868bb8f9958e34d5155437d009b72dff33fc28874c87fd42e51c0f74fdb - Transaction hash from the command “masternode outputs”.<BR>
0 - Single digit from the command “masternode outputs”.

28. Save the file and close notepad.




29. Shutdown your wallet and re-open your wallet.

30. Go to “Settings”. 
Click "Encrypt Wallet"

31. Shutdown your wallet ***AGAIN*** and re-open your wallet.

32. Go to “Settings”
Click “Unlock Wallet”

33. Enter your wallet passphrase and unlock your wallet.

34. Go to "Masternodes" tab.
you should see your masternode listed

34a. If status says: "MISSING" wait 5 minutes and click "Start MISSING" button

34b. if error i.e. "must wait for sync to finish"
wait another 5 minutes and try again
rinse, repeat until status says "PRE_ENABLED"

35. Once "PRE-ENABLED" leave alone until status shows "ENABLED" (approx 5-30 mins)
<BR>
*****if any other errors try:******<BR>
Go to “Tools”. 
Click “Debug console”.

Start your masternode MANUALLY using the command:
masternode start-alias MN1

It will take 5-30 minutes to activate your masternode.

***ONCE ACTIVATED MASTERNODE WILL SHOW UP THE LIST AS ENABLED AND YOU WILL BEGIN RECIEVING REWARDS AFTER A FEW HOURS USUALLY.***




