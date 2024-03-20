# Proebsting's Law Paper

[Link](https://gwern.net/doc/cs/algorithm/2001-scott.pdf).

Proebsting's Law is stated as a kind of joke that compiler optimizations doubles programs performance every 18 years, compared to Moore's Law in wich hardware doubles performance (by increasing the numbers of transistors) every 18 months.

The paper, written in 2001, uses the SPEC95 benchmarks for comparing performance of an "old" compiler vs a "new" one. In reality what it does is compile the same set of programs with `-03` and with `-O0` and consider that the latter is equal to code as it would have been produced by a compiler in 1965, when compiler optimization research started.

I don't feel particularly comfortable with that comparison, because it is not fair, Im sure compilers were much simpler in 1965 than in 2001 and did not produce the same quality of code. But I also recognize the imposibility of comparing compilers 18 or more years apart. An "old" compiler would target specifically old hardware and would not be able to take advantage of modern instructions, that performance hit is in no way fault of the old compiler, because it doesn't have a way to know about the new instructions. The new compilers, aware of AVX512 for example, would be able to produce much faster programs, but all the merit goes to the hardware that now has much faster instructions.

Even in that almost 40 year lifespan of optimizations from `-O0` to `-O3` we only get 3.3x performance improvement for standard programs and 8.1x for scientific ones. Which suggests a lower rate of improvement than that posed by Proebsting.

This paper serves as a cautionary tale, that the focus on development compiler techniques is much better spent on language design and programmer's productivity rather than squeezing the last bit of performance, because there just isn't that much to squeeze. Though, nobody wants to leave a 3.3x performance improvement on the table if one can have it. 

# Article

[Link](https://zeux.io/2022/01/08/on-proebstings-law/)

The conclusion of the article is that Proebsting's Law should be changed to:

> Compiler Advances Double Computing Power Every 50 Years, And The Interval Keeps Growing

This comes from comparing two versions of LLVM: 2.7 and 11, which are 11 years apart. And, in general, programs only run 10-20% faster on the latest.

Nevertheless, the set of compiled program is very small and specific, the article claims that the comparison is non-scientific because it is too narrow.

It kind of doubles down on the fact that focusing on performance optimization for compilers shouldn't be a primary concern. It is just a tiny part of the puzzle in which the programmer, the hardware and the compiler interact.
