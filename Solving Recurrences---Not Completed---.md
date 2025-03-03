# Lecture 3 Solving Recurrences
<ol>
<li> <b> Recursion vs Recurrence </b></li>
 <ul><li><b> Recursion  </b> is a programming technique where a function calls itself directly or indirectly in order to solve a problem.</li></ul>
 <ul><li><b> Recurrence</b> refers to a mathematical equation or formula that describes <b>a sequence of values </b> or the <b> time complexity of an algortihm</b> by expressing each term in terms of previous terms.</li></ul>
</ol>

 ### Some Recurrences
  | Recurrences  | Formulas    |
  |---|---|
  |Fibonacci Numbers   | F(n)=F(n-1)+F(n-2)    |
  |Padovan Sequence |F(n)=F(n-2)+F(n-3)   | 
  |Pell Numbers   | F(n)=2F(n-1)+F(n-2)  |

 ### Theorems to Solve Recurrencesv


   <ol>
    <li> <b> Master Theorem </b></li>
    <ul><li>The <b> Master Theorem </b> is a method used to solve recurrence relations of this form:</li></ul>
    <ul><li> <i> T(n)=aT(n/b)+f(n)</i> </li></ul>
    <ul><li> <i> a</i> is the number of recursive subproblems in each step.</li></ul>
    <ul><li><i> b</i>is the factor by which the input size is reduced in each recursive call.</li></ul>
    <ul><li> <i> f(n)</i> represents the work done outside of recursion.(e.g.,dividing the problem,merging results,etc.)</li></ul>
    <ul><li>Cases:</li></ul><br>
        <b>Case 1:</b> If <b>f(n)=𝑂( n<sup>log<sub>b</sub><sup>a</sup> </sup> − 𝜀 ))</b> for some constant 𝜀>0,then <b>T(n)=Θ( n<sup>log<sub>b</sub><sup>a</sup> </sup>)</b> <br>
        <b>Case 2:</b> If <b>𝑓(𝑛) = Θ( n<sup>log<sub>b</sub><sup>a</sup> </sup>)</b> then <b>𝑇 𝑛 = Θ(( n<sup>log<sub>b</sub><sup>a</sup> </sup>). log 𝑛)</b><br>
        <b>Case 3:</b> If <b>𝑓 𝑛 = Ω( n<sup>log<sub>b</sub><sup>a</sup> </sup> + 𝜀))</b> for some constant 𝜀 > 0, and if 𝑎 𝑓 (𝑛/𝑏) ≤ 𝑐𝑓(𝑛) for some constant 𝑐 < 1 and all sufficiently large 𝑛, then 𝑇(𝑛) = Θ(𝑓(𝑛)). <br>
        <i>Conclusion:</i><br> If <b>f(n)</b> is larger then the solution is  𝑇(𝑛) = Θ(𝑓(𝑛)).<br>
           If  n<sup>log<sub>b</sub><sup>a</sup> </sup>is larger then the solution is T(n)= Θ( n<sup>log<sub>b</sub><sup>a</sup> </sup>)
   </ol>
    
  
  ### Examples

     

  <ol>
    <li> <i> T(n)=9T(n/3)+n</i> </li>
    <i> Solution:</i><br>The formula is: <b>T(n)=aT(n/b)+f(n)</b><br>
    So,<i> a </i> = 9,<i>b</i> = 3,<i>f(n)</i> = n. <br>
    n<sup>log<sub>b</sub><sup>a</sup> </sup>=n<sup>log<sub>3</sub><sup>9</sup> </sup> = n<sup>2</sup><br>
    <b>T(n) = Θ(n<sup>2</sup>)</b>
    <li><i>T(n)=T(2n/3)+1</i></li>
      <i> Solution:</i><br>The formula is: <b>T(n)=aT(n/b)+f(n)</b><br>
      So,<i>a</i> = 1,<i>b</i> = 3/2,<i>f(n)</i> = 1.<br>
      n<sup>log<sub>b</sub><sup>a</sup> </sup>=n<sup>log<sub>3/2</sub><sup>1</sup> </sup> = n<sup>0</sup>=1 <br>
      <b>T(n) = Θ(logn)</b>
    <li><i></i></li>
      
  </ol>
    
    
    
    
    
    
