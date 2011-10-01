Official BitPenny Client Source Code (www.BitPenny.com)
based on Bitcoin 0.4.0 codebase


Purpose
===================

This source code is released with the intention of allowing community members
to inspect and customize the BitPenny Client in order to improve security and
prevent the possibility of >50% mining power attacks by the server.  
Developers are free to make changes to the code, submit pull requests, and 
develop alternate clients.  The BitPenny Client is meant to be used together 
with the BitPenny mining pool server, which is not open source.  By using this
software, you agree to do so in good faith and to not deliberately harm the
BitPenny server. 


How To Build
===================
git clone git://github.com/ForceMajeure/BitPenny-Client.git
cd BitPenny-Client/src
make -f makefile.bitpenny.unix bitpennyd

For dependencies, see doc/build-unix.txt


Sample Config File
===================
.bitpenny/bitpenny.conf

 # standard bitcoind options
 rpcuser=
 rpcpassword=
 rpcport=
 rpcallowip=
 
 # BitPenny options
 
 # set 1 for pooled mining and 0 for solo mining
 # can be changed with "setpool true|false" rpc command
 pool=1
 poolhost=bitpenny.dyndns.biz
 poolport=8338
 
 # pooluserid must be a valid Bitcoin address
 # this address is used for both pooled and solo mining
 # nothing is stored in the local wallet.dat
 # it is NOT advised to use the bitpennyd client as a wallet
 
 pooluserid=
 
 # time interval in milliseconds to calculate shares per second
 # can be changed via "setpoolinterval" rpc command
 statsinterval=60000
 
 # bitpennyd automatically defaults to solo mining mode whenever the server is unavailable
 # set the following parameter to 1 if you'd rather receive an HTTP 500 error instead of switching to solo mode
 # get/setpooldisablesolo rpc commands are also available
 # please note that bitpennyd provides an x-poolmode HTTP header to indicate the type of work returned
 # the header value is set to 1 when pool work is returned, and 0 when solo work is returned
 # this can be used by miners and proxies for further processing
 pooldisablesolo=0