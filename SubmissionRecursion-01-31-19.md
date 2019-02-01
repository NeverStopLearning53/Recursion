# **Exercises**
# **Questions**

##### **1 What is recursion?**
It is a programming technique for iterating (the repetition of a process in a computer program, usually done with help of loops.) over an operation by having a function call itself over and over until it arrives at some result.

##### **2 When would a programmer want to write a recursive function instead of an iterative one?**
Good question ... Iterative functions are the preferred choice generally between the two because the iterative function is more space efficient than the recursive. Sometimes though the Iterative is very complicated and using the recursive solution can result in cleaner less complicated code so it would be the better choice.

##### **3 What is a base case and what is its role in a recursive function?**
A base case is the case in recursion where the answer is known or we can say the termination condition for a recursion to unwind back.

##### **4 What would happen if a programmer did not utilize a base case within a recursive function?**
Without a base case our recursive function will run forever or generate a stack overflow error.

#**Code Practice**
##### **Create a recursive function that will take a positive integer parameter `n` and return the factorial of `n`.**

```
var factorial = function pf(n) {
    if (n <= 1) {
        return 1;
    } else {
        return n * pf(n - 1);
    }
};

var fac = factorial;
factorial = null;
console.log(fac(5));
```

