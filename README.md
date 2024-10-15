# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

# MY ANSWER, MAXIE M.

**Recurrence Relation**  
$T(n)$ will represent the time complexity of function for input size $n$ 

$$
T(n) = 
\begin{cases}
1 & \text{if } n \leq 1 \\
3T\left(\frac{n}{3}\right) + n^5 & \text{if } n > 1
\end{cases}
$$

Next we will expand the recurrence:

$T(n) = 3T\left(\frac{n}{3}\right) + n^5$

**first iteration** 

$3T\left(\frac{n}{3}\right) = 9T\left(\frac{n}{9}\right) + 3\left(\frac{n}{3}\right)^5 = 9T\left(\frac{n}{9}\right) + \frac{n^5}{243}$

**second iteration** 

$9T\left(\frac{n}{9}\right) = 27T\left(\frac{n}{27}\right) + 9\left(\frac{n}{9}\right)^5 = 27T\left(\frac{n}{27}\right) + \frac{n^5}{59,049}$

**$i-th$ expression**
At level $i$, there will be $3^i$ subproblems (each with size $\frac{n}{3^i}$) 

**Work done at this level**

$3^i T\left(\frac{n}{3^i}\right) + 3^i\left(\frac{n}{3^i}\right)^5 = 3^i T\left(\frac{n}{3^i}\right) + \frac{n^5}{3^{4i}}$

**Total Work**
Is given by the sum across all levels 

$T(n) = n^5 \left(1 + \frac{1}{3^4} + \frac{1}{3^8} + \dots \right)$

**note: The sum of this geometric series converges to a constant**

With this the overall complexity will be dominated by work at the top level. The work at the top level is $n^5$. Making the time complexity of this function $T(n) \in \mathcal{O}(n^5)$. Overall coming to the conclusion that the tight bounf on the runtime of the **mystery(n)** function is $\mathcal{O}(n^5)$. 


# Plagiarism Statement
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

# Resources: 
**Repositories:** recurrence-analysis-ClaytonBrown4741 
