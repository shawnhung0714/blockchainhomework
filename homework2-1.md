# Review of ***Bitcoin: A Peer-to-Peer Electronic Cash System***

## Student Info

ID: P06922004
Name: 洪軒治
## Summary
It is well known that Bitcoin has become a very popular financial merchandise today. Starting from 2009, the price of Bitcoin was only less than one dollar when published, but it just broke 10000 dollars in 2018. It is so popular that CPOE even announced future of Bitcoin not long ago. On the other hand, this paper explains, although not everything, the foundamental theories of trust mechanism in Bitcoin.

First of all, this paper describes how to use cryptographic hash to make a transaction record. To secure transactional trust, one transaction contains hash value from last trasaction, owner's public key, and owner's signature. The hash value of a transaction is generated from value of owner's public key, hash of last transaction, and last owner's signature. In fact, these elements come from crytopgraphic theorem that ensure these records are non-repudiation and no participant can mess up these trust mechenisms.

Sencondly, in order to keep these trust mechenisms to be decentralized, a proof-of-work (POW) system has been created to ensure incentive of miner and data integrity of transaction records. More precisely, as miners compete to provide their versions of records, they must provide the correct POW hash value before commiting; however, only competence is not enough to attract any miner to involve this system, so this system gives reward to miner to be the incentive. As a result, every participant receives his or her benefit while paying some effort to keep this system living.

Finally, the author gives some methmatical proof of this system. This proof start from the fundamental Binomial random walk, giving following statements:

    p = probability an honest node finds the next block
    q = probability the attacker finds the next block
    qz = probability the attacker will ever catch up from z blocks behind

$$
q_z = \begin{cases}
   1 &\text{if } p \le q \\
   (\frac{a}{b})^z &\text{if } p > q
\end{cases}
$$

the attacker's potential progress will be a Poisson distribution with expected value:

$$
\lambda = z\frac{q}{p}, \text{assume p > q}
$$

we multiply the Poisson density for each amount of progress:

$$
\sum_{k=0}^\infty\frac{\lambda^ke^{-\lambda}}{k!}\cdot
\begin{Bmatrix}
   (\frac{q}{p})^{z-k} &\text{if } k \le z \\
   1 &\text{if } k > z
\end{Bmatrix}
$$

Rearranging to avoid summing the infinite tail:

$$
1 - \sum_{k=0}^z\frac{\lambda^ke^{-\lambda}}{k!}(1 - (q/p)^{z-k})
$$

the author used this conclusion with some practical program to emulate the result and found out that the probability drop off exponentially with z, so that it prevents the attacker from exploiting this system from the methmatical theories.

## Reflection
This paper describes how a sophisitical, decentralized ledger system is constructed, and how the author uses academic theorem and methodology to secure this system from attacking. This idea has finally become a  new  financial product or currency without centralized back to the real world; nevertheless, this paper does not mention how much resource, such as computing power and electricity, need to keep this system running, and the impact to financial economy of real world. Therefore, many innovation, like Ethereum, have been created to improve the drawbacks of Bitcoin.