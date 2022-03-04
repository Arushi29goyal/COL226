# COL226 Assignment 3

-Arushi Goyal, 2020CS50418</br>

This is the readme file for COL226 Assignment 3: Abstract Syntax Trees(ASTs) for WHILE.</br>
I have used ML-Lex and ML-Yacc tools for performing lexing and parsing operations.</br>

## AST Datatype definition

* ID: type string
* Program: 
  * PROG of type ID * Block
* RelOp:
  * LT(Less than) of type Exp * Exp
  * LEQ(Less than or equal) of type Exp * Exp
  * GT(Greather than) of type Exp * Exp
  * GEQ(Greater than or equal) of type Exp * Exp
  * EQ(Equal) of type Exp * Exp
  * NEQ(Not equal) of type Exp * Exp
* Type:
  * INT(Integer)
  * BOOL(Boolean)
* BinaryOp:
  * AND
  * OR
  * PLUS(Addition)
  * SUB(Subtraction)
  * DIV(Division)
  * TIMES(Multiplication)
  * MOD(Remainder)
* UnaryOp:
  * NOT
  * NEG(~ sign: denotes negation of a numeral)
* Declaration:
  * DEC of type Variable * VariableList * Type
* Block:
  * BLK of DeclarationSeq * CommandSeq
* DeclarationSeq:
  * DECSEQ1 of Declaration
  * DECSEQ2 of Declaration * DeclarationSeq
* CommandSeq:
  * CMDSEQ1 of Command
  * CMDSEQ2 of Command * CommandSeq
* VariableList:
  * VARL1 of Variable
  * VARL2 of Variable * VariableList
* Command:
  * SET(":=") of Variable * Exp
  * ITE(If then else) of Exp * CommandSeq * CommandSeq
  * WH(While loop) of Exp * CommandSeq
* Exp:
  * IEXP(Integer Expression) of int
  * BEXP(Boolean Expression) of bool
  * BINEXP(Binary Expression) of BinaryOp * Exp * Exp
  * UNEXP(Unary Expression) of UnaryOp * Exp
  * CONDEXP(Conditional Expression) of RelOp * Exp * Exp
* Variable: 
  * VAR of ID
 
 ## Context-free Grammar
 
 * Start ::= Program
 * Type ::= INT|BOOL
 * Program ::= "program" Identifier ":=" Block
 * Block ::= DeclarationSeq CommandSeq
 * Declaration ::="var" VariableList : Type ;
 * DeclarationSeq ::= {Declaration}
 * VariableList ::= Variable{"," V ariable} 
 * CommandSeq1 ::= {Command ";"}
 * CommandSeq ::= {CommandSeq1}
 * Command ::= Variable ":=" Expression | "read" Variable | "write" Expression | "if" Expression "then" CommandSeq "else" CommandSeq "endif" |
"while" Expression "do" CommandSeq "endwh"
 * Expression ::= Expression "+" Expression|Expression "-" Expression|Expression "x" Expression| Expression "/" Expression|Expression "%" Expression
 |Expression ">" Expression|Expression ">=" Expression|Expression "<" Expression|Expression "<=" Expression|Expression "=" Expression|Expression "<>" Expression
 | Expression "&&" Expression |Expression "||" Expression | "!" Expression | (Expression) | Variable | Numeral | "~" Numeral
* Variable ::= Identifier


 ## Acknowledgements
 
 1. Andrew W. Appel, James S. Mattson, David R. Tarditi: User's Guide to ML-Lex and ML-Yacc</br>
 The file compiler.sml has been taken from the example program pi in this pdf. I have taken few references from .lex files of the pi program to write my own ast.lex.
 2. https://github.com/arch1902/COL226-PL-Assignments (Github profile of IITD Senior: Arpit Chahuhan)</br>
 I have taken references for the syntax for grammar definition of the WHILE language from .yacc files in this repository.</br>
 
 
 
 
 
  
