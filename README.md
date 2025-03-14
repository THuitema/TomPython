# TomPython
A basic interactive Python interpreter written in Rust

<img src="example.png" alt="example code" width="400"/>

## Description
I gained inspiration for this project after completing CMSC 330 (Organization of Programming Languages) at UMD. My favorite project in the class was making an OCaml interpreter, so I wanted to explore the topic further with this project.
I decided to write this interpreter for Python because it is a widely used language, so further understanding its type system and syntax would benefit me. I wrote it in Rust because we briefly studied it in CMSC 330, and I wanted to become more proficient at it.
Rust appealed to me because it emphasizes memory safety and has useful pattern-matching features.

TomPython incorporates numerous Python features. Available types are integers, floats, booleans, and strings. TomPython allows for variable assignment, if-else statements, functions, and mathematical expressions.
Looking forward, I would like to add functionality for loops (for and while loops), list types, and classes.

## Context-Free Grammar
Statement -> AssignStatement | IfStatement| FunctionStatement | Expr 

AssignStatement -> ```TokVar``` = Expr

IfStatement -> ```if``` Expr ```:``` ```TokIndent``` Statement+ ```TokDedent``` ElseStatement<br>&nbsp;&nbsp;&nbsp;&nbsp;*Indent must be same length as dedent*

ElseStatement -> ```else``` ```:``` ```TokIndent``` Statement+ ```TokDedent```

FunctionStatement -> ```def``` ```TokVar``` ```(``` (```TokVar``` ```TokComma``` )* ```)``` ```:``` ```TokIndent``` Statement+  ```TokDedent```

ReturnExpr -> ```return``` Expr | Expr

Expr -> AndExpr ```or``` Expr | AndExpr

AndExpr -> EqualityExpr ```and``` AndExpr | EqualityExpr

EqualityExpr -> RelationalExpr EqualityOperator EqualityExpr | RelationalExpr <br>&nbsp;&nbsp;&nbsp;&nbsp;EqualityOperator -> ```==``` | ```!=```

RelationalExpr -> AdditiveExpr RelationalOperator RelationalExpr | AdditiveExpr <br>&nbsp;&nbsp;&nbsp;&nbsp;RelationalOperator -> ```<``` | ```>``` | ```<=``` | ```>=```

AdditiveExpr -> MultiplicativeExpr AdditiveOperator AdditiveExpr | MultiplicativeExpr ```TokUnaryMinus``` NumericalExpr | MultiplicativeExpr <br>&nbsp;&nbsp;&nbsp;&nbsp;AdditiveOperator -> ```+``` | ```-```

MultiplicativeExpr -> UnaryExpr MultiplicativeOperator MultiplicativeExpr | UnaryExpr <br>&nbsp;&nbsp;&nbsp;&nbsp;MultiplicativeOperator -> ```*``` | ```/```

UnaryExpr -> ```TokUnaryMinus``` FunctionCallExpr | ```not``` FunctionCallExpr | FunctionCallExpr

FunctionCallExpr -> ```TokVar``` ```(``` (Expr ```,```)* ```)``` | PrimaryExpr

PrimaryExpr -> ```TokInt``` | ```TokFloat``` | ```TokBool``` | ```TokVar``` | ```(``` Expr ```)```

## Getting Started
1. Clone the git repository
   ```shell
   git clone https://github.com/THuitema/TomPython.git
   ```
2. Compile the rust files
   ```shell
   cargo build
   ```
3. Run the interpreter
   ```shell
   cargo run
   ```
