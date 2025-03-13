# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.

Add your answers to this markdown file.

“I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.”-Andrew Thomas

Sources

1.) 

### Question 1
*List 3 reasons why asymptotic analysis may be misleading with respect to actual performance in practice.*

-Reason 1: Dropping constants hides differences in performace
  
  When we are analyzing the asymptotic complexity of an algorithm we always drop the constants before computing. This is generally because we don't care about the specifics of how fast something runs, just how fast it runs under some threshold. In the case of Big O we care if that function applies to the mathematical definition:
  
   $T(n)\in O(f(n))$ if if there are positive constants $c$ and $n_0$ such that $T(n) \leq c f(n)$ $\forall$ $n\geq n_o$.

   This is great for generalizations about the speed of an algorithm but when put into practice can be misleading.

   For example imagine you had an algorithm that was $T(n)=10log(n)$ and another algorithm that was $G(n)=100000log(n)$.
   When we look at the time complexity of $T,G$ we instantly know they are exactly the same but if we were actually running both algorithms on a system then G would be big optimization problem and would end up taking way longer than T. That is to say even though the complexity is the same it is more practical to use the one with the smaller constant in a real-life siutation.

   Thus we see one reason asymptotic complexity can be misleading.

-Reason 2: Time complexity is somewhat general

Time-complexity is essentially a mathematical set contained by some given criteria. Which is to say maybe we only want functions less than or equal to(Big O), greater than or equal to(Big-$\Omega$). The time complexity only tells us that any given function $T(n)$ for some algorithm fits a criteria of a set, and because a lot of algorithms can fit into that set it doesn't tell us much about how practical it is, or how it works.

For example:

 Maybe your implementing something into a database and you need store information efficiently with respect to memory, so you choose an in-place algorithm to use less memory. However you also notice that its asymtotic complexity is worse than that of an alternative non-in-place algorithm so you decide to go with the algorithm with better time complexity instead. You use this algorithm and eventually you start to run out of memory because your not storing your data-operations efficiently. You then switch back to the slower algorithm and everything works out, becauase your now storing data efficiently. Which goes to show that a "good" time complexity doesn't always mean you get what you want.

 This is a good example of why the general nature of asymtotic complexity doesn't reaveal much about its practically, especially because algorithms can and need to be very specific for different goals.

Reason 3:  Time complexity can be relative:

The last and final reason time complexity can be misleading really stems from the definition.  so lets state it again,

$T(n)\in O(f(n))$ if if there are positive constants $c$ and $n_0$ such that $T(n) \leq c f(n)$ $\forall$ $n\geq n_o$.

Above we can see that we pick two postive constants, one $c$ and one $n_o$.  We have already talked about what c does, its just a scalar value of $f(n)$. However the purpose $n_o$ serves a different purpose. What $n_o$'s condiition instead says is that: We choose some input size $n_o$ and then the condition $T(n) \leq c f(n)$ is true after or exactly at that point, however it can be completely untrue before that point. What this means is that your algorithms time complexity could potentially be something different before it hits $n_o$ value. This can be very misleading and if you don't account for this before you choose to use a certain algorithm it may not yield the results you expect for all input sizes.



## Question 2
**Suppose finding a particular element in a binary search tree with 1,000 
  elements takes 5 seconds. Given what you know about the asymptotic complexity*
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.*

The time compliexity for search of a Binary tree is: $O(Log(n))$

Thus by definition for a given $T(n)\in O(log(n))$, we have that $\exists $ $n_0,c$ such that $T(n)\leq c\cdot log(n)$ $\forall $ $n\geq n_o$. Where c and $n_o$ are positive constants.

Then if we choose our c carefully we can scale it such that it equals 5 seconds and this will allow us to figure out the case for $n=10,000$.

Given our initial input size $n=1000$ we have:

$C\cdot log_2(1000)=5$

$=C=\frac{5}{log_2(1000)}$=0.5017

Checking this let $C=0.5017$

$0.5017\cdot log(1000)=5$ seconds.

Now we can plug this in for $n=10,000$:

Choose  $C=0.5017$

$0.5017 \cdot log(10000)=6.66$ seconds.


## Question 3

*You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.*

$T(n)=\frac{n}{100}$


  Reason 1: Differences in software behavior

 If we initally run our computer with no tabs open and nothing else on the computer running. Other than what is necessary of course, then lets say our computer took 5 seconds as it did above. However the next time we run it we have two different browsers open with several tabs and a video running in the backgroud then our program could end up potentially taking 100 seconds. This is because the computers resources such as the ram are taken up and only a small amount can be allowcated to the task of the search.

  Reason 2: Different Hardware

  If we were to for some reason run our search algorithm on a raspberry pi or something with very low computional power then our algorithm could end up taking much longer than it runs on a powerful labtop or computer. Hence it took 100 seconds

  Reason 3: Different Data types
  
  Say our BST was composed of nodes represetning different audio files and we had to find a file with a specific frequency. This would require more computional power because we would be running a more complex search algorithm and we would have to search the entirety of each audio file. Therefore our search algorithm took longer. This could also apply to other complex data-types such as Videos or images.
