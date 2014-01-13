Unus Mundus
===========
slowpoke <mail+git@slowpoke.io>
v0.1 - Draft

Overview
--------
The basic idea behind Unus Mundus is to create a decentralized build system 
which uses deterministic building to both provide assurance against backdoors 
in binary package as well as void the need for central repositories.
Volunteers can donate either CPU time or bandwith (or both) to build and/or 
distribute packages for a Linux (or other UNIX) distribution.

Concept
-------
Building
~~~~~~~~
Unus Mundus requires a basic premise to work: a way to deterministically build 
software from source; that is, if two people use the same input and same 
parameters, they will produce exactly the same output - bit-for-bit identical.  

Fortunately, a way to do this already exists: https://gitian.org/[gitian]

What's left is to implement a way to automate building arbitrary packages with 
gitian, and to distribute the work evenly over the network.

Signing
~~~~~~~
After successfully building, the system must check the result against the 
expected checksums. If they match, the builder signs the resulting package, and 
either just uploads said signature (discarding the built package), or begins 
distributing the package. This creates a web of trust, where people no longer 
need to rely on trusting a single party for security and safety, but instead 
have a great number of people verifying the promises of that single party.

Distribution
~~~~~~~~~~~~
Another incredible advantage of deterministic builds is that, since everybody 
creates the exact same packages, they can immediately offer them over P2P 
networks such BitTorrent after building, creating not only a decentralized 
build system, but also a Peer-to-Peer-repository of secure, binary packages.
