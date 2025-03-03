# Time Complexity for Recursive Algorithms
## What is Recursion?
  - *Recursion* is a programming technique where a function calls itaelf directly or indirectly in order to solve a problem.
  - Recursion typically involves two components: the *base case(s)* and the *recursive cases*.
  - The base case provides a *termination condition* for the recursion.
## How to Solve a Problem in a Recursive Way?
  - **Divide and Conquer Strategy**
  - Divide problem into *smaller* parts and solve them independently then combine results.
### Example
   - Computing 1+2+3+....+N Recursively
``` C++
    int Sum(int n){
         if(n==1) return 1;
         return Sum(n-1);
    }
```

  <ul><li>Let's break down the code. </li></ul>
  1. **if(n==1) return 1;**
     - This code runs just 1 time when n=1.
  2.  **return Sum(n-1);**
      - This code runs (n-1) times until it reaches n=1.
      - To combine results,we need 1 step.
  3. *Result*
      - Time complexity for this algorithm:
      - *T(n)=1* if n=1.
      - *T(n-1)+1* if n>1.
### Example 
  - Compute the sum of N numbers A[0,1,2.....,N-1]
    1. We need the base *case(s)*:
       - Array has one element : return(A[0]);
    2. We also need the *recursive case*:
       - Compute the sum of the first N-1 numbers then merge them adding the last number.
``` C++
    int Sum(int N,int A[]){
         if(N==1) return A[0];
         return Sum(A,N-1)+A[N-1];
    }
```
   <ul><li>Let's break down the code:</li><ul>
   1. **if(N==1) return A[0];**
      - This code runs 1 times when n=1.
   2. **return Sum(A,N-1)+A[N-1];**
      -  This code runs n-1 times until it reaches n=1.
      -  We need 1 step to combine results. 
   3. *Result*
      - Time complexity for this algorithm:
      - *T(n)=1* if n=1.
      - *T(n-1)+1* if n>1.
  ### Example 

  
   - We can solve the above problem in different ways.  
  <ol>
    <li>We need the base *case(s)*:</li>
    <ul> <li> Array has one element : return(A[0]); </li></ul>
    <li>  We also need the *recursive case*:</li>
    <ul> <li> We can divide the array into two parts:</li></ul>
    <ul> <li> middle = n/2. </li></ul>
  </ol>
  
```C++
   int Sum(int A[],int N){
   if(N==1) return  A[0];
   int middle=N/2;
   int localSum1=Sum(&A[0],middle);
   int localSum2=Sum(&A[middle],N-middle);
   return localSum1+localSum2;
   }
```

   <ul> Let's break down the code.</ul>
   <ol>
    <li> <b>if(N==1)  return(A[0]);</b></li>
    <ul> <li> This code runs 1 time when n=1. </li></ul>
    <li> <b> int middle = N/2;</b>
    <ul> <li> This code takes just 1 step.</li></ul>
    <li> <b>int localSum1=Sum(&A[0],middle);</b> </li>
    <ul> <li>This code contains a recurrence,it splits the problem into two halves and calls itself one time. </li></ul>
    <li><b> int localSum2=Sum(&A[middle],N-middle); </b></li>
    <ul> <li> This code contains a recurrence,it splits the problem into two halves and calls itself one time. </li></ul>
    <li><b> return localSum1+localSum2;</b></li>
    <ul><li> This code returns constant values so it takes 1 step.</li></ul>
     <li><i> Result:</i>  </li>
     <ul> <li> <i> T(n)=1 </i>  if n=1</li></ul>
     <ul> <li> <i>2T(N/2)+1 </i> if n>1 </li></ul>
     </ol>

### Note
   <ul> <li> A recurrence is a mathematical equation that defines a function in terms of smaller instances of itself. </li></ul>

### Example
   <ul> <li> Computing A^n Recursively:</li></ul>
   <ol>
     <li> Base cases:</li>
     <ul> <li> n=0 -> return 1</li></ul>
     <ul> <li> n=1 -> return a</li></ul>
   </ol>
   
```C++
   int Power(int a,int n){
   if(n==0) return 1;
   if(n==1) return a;
   return a*Power(a,n-1);
   }
```
   <ul> Let's break down the code.</ul>
   <ol>
    <li> <b>if(n==0)  return 1;</b></li>
    <ul> <li> This code runs 1 time when n=0. </li></ul>
    <li> <b>if(n==1) return a;</b>
    <ul> <li> This code also runs 1 time when n=1.</li></ul>
    <li> <b> return a*Power(a,n-1);</b> </li>
    <ul> <li>This code makes a recursive call,recuding n by 1.</li></ul>
    <li><i> Result:</i>  </li>
     <ul> <li> <i> T(n)=1 </i>  if n=1</li></ul>
     <ul> <li> <i>T(n-1)+3 </i> if n>1 </li></ul>
     </ol>
     
### Example
   <ul> <li> Computing A^n Recursively 2:</li></ul>
   <ol>
     <li> Base cases:</li>
     <ul> <li> n=0 -> return 1</li></ul>
     <li> Recursive step:</li>
     <ul><li> Compute a^n/2 recursively.</li></ul>
     <ul><li> If n is even,return a^n=a^((n/2)^2)</li></ul>
     <ul><li> If n is odd,return a^n=a*a^((n/2)^2)</li></ul>
   </ol>
   
```C++
   int Power(int a,int n){
   if(n==0) return 1;
   int half=Power(a,n/2);
   if(n%2==0)return half*half;
   else return a*half*half;
   
   }
```


   <ul><li>Let's break down the optimized code:</li></ul>
   <ol>
     <li><b>if(n == 0) return 1;</b></li>
     <ul><li> This is the base case, taking O(1) time.</li></ul>
     <li><b>int half = Power(a, n / 2);</b></li>
     <ul><li> This computes <i>Power(a, n/2)</i>, reducing <i>n</i> by half.</li></ul>
     <li><b>If n is even, return half * half;</b></li>
     <ul><li> This squares the result, taking O(1) time.</li></ul>
     <li><b>If n is odd, return a * half * half;</b></li>
     <ul><li> This multiplies by <i>a</i> once more, taking O(1) time.</li></ul>
     <li><i>Result:</i></li>
     <ul><li> <i>T(n) = O(1)</i> if n = 0.</li></ul>
     <ul><li> <i>T(n) = T(n/2) + O(1)</i> if n > 0.</li></ul>
     <ul><li> <i>Final complexity: O(log n)</i>.</li></ul>
    </ol>


### Example
```C++
    int GCD(int a, int b) {
    if (b == 0) return a;
    return GCD(b, a % b);
}
```
   
  <ul> Let's break down the code:</ul>
  <ol>
    <li> <b>if(b == 0) return a;</b></li>
    <ul> <li> This is the base case, taking O(1) time.</li></ul>
    <li> <b>return GCD(b, a % b);</b></li>
    <ul> <li> This calls GCD recursively with <i>b</i> as the new first parameter and <i>a % b</i> as the new second parameter.</li></ul>
    <li><i>Result:</i></li>
    <ul> <li> <i>T(n) = O(1)</i> if b = 0.</li></ul>
    <ul> <li> <i>T(n) = T(a % b) + O(1)</i> otherwise.</li></ul>
    <ul> <li> <i>Final complexity: O(log min(a, b))</i>.</li></ul>
   </ol>

          
    
      
      
  
      
    
    
    
  
   
