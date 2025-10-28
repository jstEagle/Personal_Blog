Quantum computing, much like fusion energy is a a field of technological innovation the exhibits a phenomenon where every 2-3 years it get a brief moment in the media limelight.

![](Pasted%20image%2020251027125246.png)
And well.... its that time again.

### Motivation
I just want to preface the rest of this article by saying that I have absolutely **no** financial interest in any of this. I am not invested in any of the companies that may be mentioned and I don't have any long or short exposure on any of the stocks mentioned.

If there is something that really grinds my gears. It's media outlets blowing up tech news *way* out of proportion by writing sensationalist posts about new developments in a field. As we saw in the last few months with quantum computing. As a symptom of many people being exposed to these advanced technical concepts; with the added ability to jump in on the hype by buying in on these companies through the convenience of their phone. There is a lot of misinformation circulating about quantum computing.

So lets clear up what quantum computers really are. What they can and can't do. And why they aren't going to make "AI faster".

### What is a Quantum Computer?
A **quantum computer** is a type of computer that exploits some *really* cool quirks of [quantum mechanics|Physics that focuses on interactions between individual particles at an atomic or smaller level.], such as [superposition|When a particle (system) exists in multiple states at once until measured], [entaglement|When two or more particles become linked so that measuring one instantly affects the other, at any distance apart.], and [interference|When quantume states combine in ways that amplify some outcomes and cancel others (just like waves) guiding probabilities towards a certain result.] - to perform calculations by exploring **many** possibilities in *superposition*. The actual power comes from **interference patterns** that bias outcomes (not from parallel universes literally computing all results).

This all sounds incredibly complicated. And it is!
But the main thing to know is that it works fundamentally different to normal computers. You can think of it as preparing a bunch of special quantum bits (qubits) that explore many possible solutions at once, and then, using clever tricks, extracting the right answer from all those possibilities.

### Is a Quantum Computer actually useful?
In short: yes. However there is more nuance to this than Google, IBM, Microsoft and every major tech media outlet would have you believe. Quantum computers are very good at very specific class of problems that are exponentially hard to run on traditional computers, but have some algorithm that can take advantage of all these quirks to allow for a good mapping to quantum principles.

In computer science, there is the concept of [Algorithm Complexity|This measures how the resources an algorithm needs, like time or memory, grow as the size of the input grows.]. Complexity is a very useful measurement tool of how good an algorithm is. You can imagine this like two people looking for a book in a library using different algorithms. The first one simply looks into the catalogue and finds the bookshelf where the book is and then searches that one. The second person just looks through all of the bookshelves until they find the right book.


![](Untitled-2025-10-27-1321.png)

If there were 100 bookshelves instead of 3, the first algorithm would still take the same time as there is still only one bookshelf to be searched. But the second algorithm would take about 30 times longer on average because it needs to search all of the bookshelves present until it finds the book.

The main goal of quantum computing is to run algorithms that on our current best computers with the best we can do, require us to search the whole library. But on a quantum computer would allow us to go straight to finding the right book. This is the kind of advantage that leads to what researches call *quantum supremacy* - when a quantum computer outperforms classical ones on a specific task.

*Note: this is a very crude way of explaining how Quantum computers can be better. It is hard to provide a better explanation without assuming some understanding of computer science and mathematics. [Read this Wikipedia article to learn more about complexity.](https://en.wikipedia.org/wiki/Computational_complexity)*

### Some common misconceptions
Now let's go over some of the common misconceptions that are floating around.

##### Quantum computers are faster!
No, they are not.
Quantum computers, as mentioned before, can take advantage of some special quirks that allows for **different** algorithms to solve problems faster than algorithms that we can run on traditional computers. The most famous of these being [Shor's Algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm) for factoring prime numbers and also [Grover's](https://en.wikipedia.org/wiki/Grover%27s_algorithm), sometimes called the "quantum search algorithm".

When it comes to actual speed, quantum computers are very slow compared to traditional computers. Speed in computers is measured how many "steps" or "cycles" the CPU can perform per second. Individual gate operations in current superconducting quantum processors run around the Megahertz range, far slower per gate than Gigahertz classical CPUs.

##### Quantum computers will change the world!
Hmmmmm..... possibly?
Quantum computers are no doubt useful in certain areas. Especially in some fields of science. But especially in recent years the advantage a quantum computer would have, has been reduced in a lot of areas.

In a lot of cases it may be useful. And even better than traditional computers. But, airlines already handle their scheduling very well. Amazon handles millions of packages a day with no issues. And video games and other physics engines simulate the world to an incredibly accurate degree. Technically yes, these could get better with quantum computers. But who is going to pay these huge amounts of money to optimise the path your uber takes on its way to deliver your burger by a couple of percent.

Of course this can be debated and argued endlessly, but from my perspective, there isn't quite as much value in a lot of these use cases as the companies building quantum computers would have you believe there is.

AI? Possibly small or uncertain improvements in specific algorithms that are heavily focused on linear algebra.

Physics simulations? Yes, but at a low level. Simulations of individual particles or cells will be more accurate which can be very useful for material science and medicine. But even here, there are already a lot of pretty good solutions already.

Other optimisations? Traveling salesman problem, Job scheduling, or large financial portfolios where every basis point counts. A lot of these problems are called [NP-hard problems](https://en.wikipedia.org/wiki/NP-hardness) which get more "expensive" or "difficult" to compute as the number of inputs gets larger in such a way that it is uneconomical or *impossible* to calculate solutions (at least in our lifetime).
*Again if you want to learn more, here are some links:*
- [QAOA (Quantum optimization algorithms)](https://en.wikipedia.org/wiki/Quantum_optimization_algorithms)
- [QUBO (Quantum unconstrained binary optimizations)](https://en.wikipedia.org/wiki/Quadratic_unconstrained_binary_optimization)

##### Quantum computers will make AI faster!
This is one I've heard a lot recently. And it's not a bad conclusion if you've just read the media articles (and there is no shame in that). In the end, AI inference - the process of taking some input tokens and calculating output tokens is just a lot of multiplication of numbers. This linear algebra on real numbers, not quantum amplitudes is not well suited to current quantum hardware. Or in other words, **a lot** of multiplication of numbers. And **a lot** of loading things in and out of memory. These constraints aren't loosened by making quantum computers, but by stuffing more transistors into more cores onto larger boards called GPUs.

As mentioned earlier, some algorithms used in training or optimisation of AI models may improve with better quantum computers. But those are still a while away.

### Quantum computers are NOT HERE yet.
No matter what Google would like you to believe. The currently largest quantum computing companies manufacture processors with very few qubits, a couple hundred to a couple thousand. And these are what are called **Physical Qubits**. The raw qubit implemented physically (e.g. a superconducting loop, trapped ion, etc). These have very large error rates, meaning that they are very inconsistent and not very usable. The **Logical Qubit** is the end goal. A *fault-tolerant*, *error-corrected* qubit built from many physical qubits (via quantum error correction). These are not achievable at scale yet and are still very experimental. So the numbers you are hearing in the news are not even the "right" kind of qubits. **And** it is important to remember that even a couple thousand qubits are not much! Once a superposition is collapsed (i.e. the qubits just end up being read as 1's or 0's) that is only enough space to store a few numbers or maybe a couple of words or maybe barely this sentence.

Me writing this article was provoked by a piece of news I saw the other day about Google's new revolutionary breakthrough on their Willow chip. [This](https://www.nature.com/articles/s41586-025-09526-6) paper which was being hailed as an incredible breakthrough in quantum computing by showing one of the first signs of "Quantum Supremacy". Was really just a contrived science experiment so specifically tailored to work on their quantum computer that it would have taken *an estimated* 13,000x longer on a traditional computer - though such comparisons depend heavily on simulation methods.

In essence they designed a very specific physics experiment that can be set up and measured on their quantum chip but is too complex for classical supercomputers to simulate efficiently.

![](Pasted%20image%2020251028212700.png)
*Not the Google quantum computer. Just here for illustration*

### Cryptography - actually pretty scary
This is where quantum computers actually get really interesting and yes, pretty scary. The world is built around encryption algorithms that keep **your data safe**. If you are sending a message to your friend, streaming a movie on Netflix or interacting with any of the most popular blockchains. You rely on encryption algorithms.

Most of these algorithms were implemented circa 30 or 40 years ago and a lot of the most common ones used today are quantum vulnerable. Most prevalent are:
- **RSA** - widely used for encryption and digital signatures, it is vulnerable because its security relies on the difficulty of factoring large prime numbers.
- **ECC** - A more modern and efficient alternative to RSA that is also vulnerable. Its security is based on the difficulty of the **Elliptic Curve Discrete Logarithm Problem**. *This is what secures Bitcoin and Ethereum using [secp256k1](https://en.bitcoin.it/wiki/Secp256k1]) and Solana using [Ed25519](https://en.wikipedia.org/wiki/Curve25519) which has some design advantages that make it more secure in practice than secp256k1*
- **Diffie-Hellman** - Used for secure key exchange (everything on the internet pretty much). It is vulnerable to quantum attacks that can solve the discrete logarithm problem.
- **DSA** - Similar to RSA and ECC, DSA is a digital signature algorithm that is vulnerable to quantum attacks.

These algorithms are all in danger if [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm) can be run on quantum computers with enough qubits. *Technical note: the complexity of Shor's algorithm is $O((\log N)^3)$ which means that over 1 million qubits would be needed to break SHA-256. And the estimate is about 13 million to break a 256-bit ECC public key in 24 hours.*

And so again, we are still a long time away from it being feasible to crack any kind of meaningful encryption. Some of the more (very) optimistic estimates range from 2-3 years. Personally I wouldn't be surprised if it took more than 10 years at least. However, progress is being made everyday and I won't claim to understand how AI and other advancements will affect the speed of development of these systems and algorithms.

Another important thing to note before everyone freaks out is that there are quantum secure encryption algorithms that simply use different approaches to encrypt data that cannot be cracked by quantum computers. Governments have started implementing these a while ago, and if this becomes any real threat, everyone will quickly scramble to switch everything over to these different encryption methods and a lot of the advantage will be gone.

### Conclusion
I've spent a long time ranting, seemingly trying to convince you that quantum computers aren't "good". **They will be!** And most importantly they are *incredibly* cool. Even the name sounds like it's straight out of Star Trek. But recently, things have just been blown out of proportion too much for my liking. I just don't like when fact and hype are at odds with each other.

Quantum computing isn't the end of classical computing - it's the sequel nobody green-lit but everyone's curious about. The plot's slow, the budget's enormous, and half the cast doesn't know their lines yet.

One day it might win awards. For now, it's mostly special effects and potential energy.

And that's okay - revolutions rarely start with fireworks; they usually start with error correction.

___

If you enjoyed reading this article. And have a decent understanding of mathematics. I would highly recommend you watch [this video](https://www.youtube.com/watch?v=RQWpF2Gb-gU) going a bit deeper into how quantum computing actually works by explaining Grover's algorithm.