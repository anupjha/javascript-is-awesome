### if statement
```javascript
if (condition)
   statement1
[else
   statement2]
```
### multiple if…else
```javascript
if (condition1)
  statement1
else if (condition2)
  statement2
else if (condition3)
  statement3
...
else
  statementN
```
### nested if…else
```javascript
if (condition1)
  statement1
else
  if (condition2)
    statement2
  else
    if (condition3)

To execute multiple statements within a clause, use a block statement { ... } to group those statements. In general, it is a good practice to always use block statements, especially in code involving nested if statements
```
### switch statement
```javascript
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```
### conditional (ternary) operator
```javascript
condition ? exprIfTrue : exprIfFalse

The ternary operator is right-associative, which means it can be "chained" in the following way, similar to an if … else if … else if … else chain:
return condition1 ? value1
         : condition2 ? value2
         : condition3 ? value3
         : value4;
```
