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

Reason 3: A good time complexity doesn't imply a good outcome for every siutation

Lastly to build upon our second reason, asymptotic complexity can be misleading when applied to certain situations such as sorting short lists.

In this last example I want to pull upon the asymptotic complexity of insertion sort($O(n^2)$) and quick-sort($O(nlog(n))$). Generally Quick-Sort is considered one of the fastest, if not the fastest sorting algorithms. However this fastestness only applies to large lists and if you were working on smaller lists you would want to actually want to use insertion sort because its actually more effiective. This is mostly because insertion sort is more memory efficient and doesn't require any complex procedures. Whereas quicksort is a little more complex and while implace does take up more memory due to recursion. When comparing small or sorted lists like this we have that quicksort has $O(n^2)$ and insertion sort has $O(n)$.

Now we if we were just to look at the general asymptotic complexity as in the begginning of the statement we wouldn't have accounted for this at all. Thus you must look at not only time complexity but also how it changes based on the task you are using it for.

Therefore we can see that the average time complexity is misleading for considering certain tasks and is depednent upon what kind of tasks you need your algorthm to perform.



## Question 2
**Suppose finding a particular element in a binary search tree with 1,000 
  elements takes 5 seconds. Given what you know about the asymptotic complexity*
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.*

Search for Binary tree: $Log(n)$

For this operation to take 5 seconds we must have $T(n)=Log(100n)$

Then we have for that 10,000 inputs takes $T(n)=Log(100(10000))=6$ seconds


## Question 3

*You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.*


  Reason 1: Our tree is actually a linked list

  If our tree is just a bunch of nodes that either increase or decrease exclusivly then we end up with a tree a resembling a linked list and our time complexity for search will be $O(n)$ slowing the search process signifiantly.

  Reason 2: Different Hardware

  If we were to for some reason run our search algorithm on a raspberry pi or something with very low computional power then our algorithm could end up taking much longer than it runs on a powerful labtop or computer. Hence it took 100 seconds

  Reason 3: Different Data types
  
  Say our BST was composed of nodes represetning different audio files and we had to find a file with a specific frequency. This would require more computional power because we would be running a more complex search algorithm and we would have to search the entirety of each audio file. Therefore our search algorithm took longer. This could also apply to other complex data-types such as Videos or images.
