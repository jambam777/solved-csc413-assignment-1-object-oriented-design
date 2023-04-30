Download Link: https://assignmentchef.com/product/solved-csc413-assignment-1-object-oriented-design
<br>
The purpose of this assignment is to practice object-oriented design to create two programs:

<ol>

 <li>An object that evaluates mathematical expressions</li>

 <li>A GUI around the artifact from (1)</li>

</ol>

You will be provided with an <em>almost complete</em> version of the Evaluator class

(Evaluator.java).  You should program the utility classes it uses – Operand and Operator – and then follow the suggestions in the code to complete the implementation of the Evaluator class. The Evaluator implements a single public method, eval, that takes a single String parameter that represents an infix mathematical expression, parses and evaluates the expression, and returns the integer result.  An example expression is 2 + 3 * 4, which would be evaluated to 14.

The expressions are composed of integer operands and operators drawn from the set +, -, *, /, ^, (, and ).  These operators have the following priority:




<table width="624">

 <tbody>

  <tr>

   <td width="312"><strong>Operator </strong></td>

   <td width="312"><strong>Priority </strong></td>

  </tr>

  <tr>

   <td width="312">+, –</td>

   <td width="312">1</td>

  </tr>

  <tr>

   <td width="312">*, /</td>

   <td width="312">2</td>

  </tr>

  <tr>

   <td width="312">^</td>

   <td width="312">3</td>

  </tr>

 </tbody>

</table>




The algorithm that is partially implemented in eval processes the tokens in the expression string using two Stacks; one for operators and one for operands (algorithm reproduced here from <a href="http://csis.pace.edu/~murthy/ProgrammingProblems/16_Evaluation_of_infix_expressions">http://csis.pace.edu/~murthy/ProgrammingProblems/16_Evaluation_of_infix_expression </a><a href="http://csis.pace.edu/~murthy/ProgrammingProblems/16_Evaluation_of_infix_expressions">s</a><a href="http://csis.pace.edu/~murthy/ProgrammingProblems/16_Evaluation_of_infix_expressions">)</a>:

<ul>

 <li>If an operand token is scanned, an Operand object is created from the token, and pushed to the operand Stack</li>

 <li>If an operator token is scanned, and the operator Stack is empty, then an Operator object is created from the token, and pushed to the operator Stack</li>

 <li>If an operator token is scanned, and the operator Stack is not empty, and the operator’s precedence is greater than the precedence of the Operator at the top of the Stack, then and Operator object is created from the token, and pushed to the operator Stack</li>

 <li>If the token is (, and Operator object is created from the token, and pushed to the operator Stack</li>

 <li>If the token is ), the process Operators until the corresponding ( is encountered. Pop the ( Operator.</li>

 <li>If none of the above cases apply, process an Operator.</li>

</ul>

Processing an Operator means to:

<ul>

 <li>Pop the operand Stack twice (for each operand – note the order!!)</li>

 <li>Pop the operator Stack</li>

 <li>Execute the Operator with the two Operands</li>

 <li>Push the result onto the operand Stack</li>

</ul>

When all tokens are read, process Operators until the operator Stack is empty.

Requirement 1: Implement the following class hierarchy

<ul>

 <li>Operator must be an abstract superclass.</li>

 <li>boolean check( String token ) – returns true if the specified token is an operator</li>

 <li>abstract int priority() – returns the precedence of the operator</li>

 <li>abstract Operand execute( Operand operandOne, Operand</li>

</ul>

operandTwo ) – performs a mathematical calculation dependent on its type

<ul>

 <li>This class should contain a HashMap with all the Operators stored as values, keyed by their token. An interface/public method should be created in Operator to allow the Evaluator (or other software components in our system) to look up Operators by token.</li>

 <li>Individual Operator classes must be sub classed from Operator to implement each of the operations allowed in our expressions</li>

 <li>Operand</li>

 <li>boolean check( String token ) – returns true if the specified token is an operand</li>

 <li>Operand( String token ) – Constructor</li>

 <li>Operand( double value ) – Constructor</li>

 <li>int getValue() – returns the integer value of this operand</li>

</ul>

<strong><em> </em></strong>

Requirement 2:

Implement the above algorithm within the Evaluator class (this implementation need not be submitted, but it is strongly recommended that you begin with this version).

Requirement 3:

Reuse your Evaluator implementation in the provided GUI Calculator (EvaluatorUI.java).

Requirement 4:

Please make sure to that class members (static or not) have the correct access modifiers. You will be graded on correctly using the private, public, protected access modifiers. Class should not be <em><u>directly </u></em>accessing data-fields of another class.

Additional Notes.

Please use the following names for the operator classes. This will make the given unit tests work better. If not, then you must modify the unit tests.

operatornameOperator

For example: AddOperator

DivideOperator

MultiplyOperator

PowerOperator

SubtractOperator

<strong><em> </em></strong>