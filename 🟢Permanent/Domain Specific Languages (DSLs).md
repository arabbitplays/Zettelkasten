# Domain Specific Languages (DSLs)

- with <mark style="background: #FFB86CA6;">domain specific modeling languages</mark>, the application structure, behaviour and requirements are specified
	- The are not general purpose like java, but less expressive and more compact and precise

## Textual Languages

- Graphical concrete syntax ist often just a subset of the abstract syntax
	- needs additional information in dialog or property windows
	- diagrams also can get very big
- with textual language, existing tools for editing text (versioning, autocompletion, highlighting, ...) can be used
- textual DLSs can be 
	- <mark style="background: #FFB86CA6;">grammar based</mark> like [[Xtext]] - define the language with a grammar definition, the [[Metamodel| Metamodel]] is then derived from the grammar
	- <mark style="background: #FFB86CA6;">mapping based</mark> like Xpand - create a metamodel and define how the elements of the model map to the syntax of the language 

### Grammar Based

- formal languages are often described with context-free grammars in the Extended Backus-Naur-Form (EBNF)
	- The grammar of the EBNF can be describen as a EBNF grammar (selfdescriptive)
- The EBNF has productions of the form
	- `non-terminal symbol = "terminal symbol" | "alternative terminal symbol";`
	- `,` for concatination, `[...]` for optional elements, `{...}` for repeating elements
- A new language also needs a parser, an editor (can also use a standard text editor) and tools that traverse the abstract syntax tree, for inking and building, ...
	- possible framework for these jobs is [[Xtext]]

---

Origin: Model Driven Software Development
References: [[Model Driven Software Development (MDSD)]]
Tags: 
Created: 06.12.2024

