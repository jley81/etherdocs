# Zero Knowledge Rollups in Ethereum
### Ori Pomerantz qbzzt1@gmail.com 

In this article you learn about the scaling problem in Ethereum, and how zero knowledge rollups can
solve it.

## Background: Consensus and Scaling

Rather than relying on a trusted central authority, blockchains rely on consensus. The problem is
that consensus doesn't scale very well. This problem is especially bad in Ethereum, because nodes don't 
just relay data, they have to actually execute the software that is embedded in contracts. In December
2019, [Ethereum averaged 12-15 transactions per 
second](https://blog.bybit.com/research-and-analysis/ethereum-blockchain-performance-and-scalability/).
This is enough to develop the technology and ecosystem, but not nearly enough for mass market adoption.


### Is This Really Necessary?

If we examine the problem, it's not really necessary for all the nodes to run the program for a 
transaction. At least one node has to actually run the program to get from the input state of the
contract to the output state, but other nodes can get the proposed output state and just verify
that it is correct. Surprisingly, this second task can be accomplished much more easily using a 
field of cryptography called [Zero Knowledge Proofs](https://en.wikipedia.org/wiki/Zero-knowledge_proof).


## Mathematical Building Blocks

To explain how it is possible to verify a program's output without running it requires several 
mathematical building blocks beyond those of basic cryptography ([hash 
functions](https://en.wikipedia.org/wiki/Cryptographic_hash_function), [private/public key
pairs](https://en.wikipedia.org/wiki/Public-key_cryptography), and so on).


### Commitments

The first building block we need to understand is commitments. A [cryptographic 
commitment](https://en.wikipedia.org/wiki/Commitment_scheme) is a message signed by a participant, that 
commits the participant to certain information without revealing that information. In the future, that 
participant can release the information, or a function of that information, and the recipients of the 
commitments will be able to verify that it is indeed the committed information.

A very simple example is signing the output of a hash function. I have some information, 
<img src="https://latex.codecogs.com/gif.latex?I" alt="I" style="vertical-align:middle">. In the 
future, I might want to prove to you that I've known 
<img src="https://latex.codecogs.com/gif.latex?I" alt="I" style="vertical-align:middle"> 
since the present time, 
<img src="https://latex.codecogs.com/gif.latex?t_0" alt="t_0" style="vertical-align:middle">. 
This information can be, for example, details of an invention I do not wish to expose yet.

I can calculate a cryptographic hash of the information, 
<img src="https://latex.codecogs.com/gif.latex?H(I)" alt="H(I)" style="vertical-align:middle">.
Then I sign this hash and send it to you with the signature. For now, you know that I committed that I know something
that hashes to 
<img src="https://latex.codecogs.com/gif.latex?H(I)" alt="H(I)" style="vertical-align:middle">.
Because of the properties of the cryptographic hash, you cannot obtain the original 
<img src="https://latex.codecogs.com/gif.latex?I" title="I" style="vertical-align:middle"> from this value.

At a later time <img src="https://latex.codecogs.com/gif.latex?t_1" alt="t_1" style="vertical-align:middle"> 
if I decide to reveal the information to you you can calculate 
<img src="https://latex.codecogs.com/gif.latex?H(I)" alt="H(I)" style="vertical-align:middle"> on your own, and see that it
is indeed equal to the hash you've received from me previously at 
<img src="https://latex.codecogs.com/gif.latex?t_0" alt="t_0" style="vertical-align:middle">.


### Polynomial Commitments

A more interesting type of commitment allows you to commit to certain information, and then provide 
the output of additional functions of it, without ever revealing the original information itself. 


### Turning Programs into Polynoms



## Plonk

https://vitalik.ca/general/2019/09/22/plonk.html
