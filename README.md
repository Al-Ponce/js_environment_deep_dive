Stop spreading VO(variable object). It's already 2023 !!  

Some blogs still sharing outdated or misleading info about **JS Environment** in 2023.  
Please be aware of!  
(!!! VO and LE shouldn't appear simultaneously.)  
(!!! **VO** is before ES5. Please **Don't** use it anymore.)  
The terms are still improving for clarification of the JS mechanism.  
Let's keep tracking!  

# JavaScript Environment Deep Dive
concept to describe the **environment**:
- Before ES5: `Variable Object`
- ES5-ES11: `Lexical Environments`
- ES12- : `Environment Records`

#### (ES5-ES11, 2009-2020)
This is what we familiar with.  
**Lexical Environment:**  
=> Consists of:
- `Environment Record`:  
records the identifier bindings of the scope.
- A `reference` to the outer *Lexical Environment*.

#### (ES12- , 2021- )
And this is the latest revision.  
**Environment Record:**  
=> Records the identifier bindings of the scope.  
- A `reference` to the outer *Environment Record*.

---

## (ES1-ES3, 1997-2009)
10.1.3 Variable instantiation
> - Every execution context has associated with it a `variable object`.  
> - Variables (and functions) declared in the source text are added as properties of the `variable object`.


---

## (ES5, 2009)
In ES5 the concept of `variable object` is replaced with `lexical environments` model.  

### 10.2 Lexical Environments  
> - A `Lexical Environment` is a specification type used to define the association of Identifiers to specific variables and functions based upon the lexical nesting structure of ECMAScript code.  
> - A Lexical Environment consists of an Environment Record and a possibly null reference to an outer `Lexical Environment`.  

> An Environment Record records the identifier bindings that are created within the scope of its associated **Lexical Environment**.

### 10.2.1 Environment Records
> For specification purposes Environment Record values can be thought of as existing in a simple objectoriented hierarchy where Environment Record is an abstract class with `two` concrete subclasses, **declarative environment record** and **object environment record**.

### 10.2.3 The Global Environment
> - The global environment is a unique `Lexical Environment` which is created before any ECMAScript code is executed.  
> - The global environment’s Environment Record is an object environment record whose binding object is the global object.  
> - The global environment’s outer environment reference is null

### 10.3 Execution Contexts
> Table 19 —Execution Context State Components  
> - **LexicalEnvironment**: Identifies the `Lexical Environment` used to resolve identifier references made by code within this execution context.  
> - **VariableEnvironment**: Identifies the `Lexical Environment` whose **environment record** holds bindings created by VariableStatements and FunctionDeclarations within this execution context.

> The **LexicalEnvironment** and **VariableEnvironment** components of an execution context are always `Lexical Environments`.
  
(↓ removed from ES11)  
> When an execution context is created its LexicalEnvironment and VariableEnvironment components initially have the same value.  

(↓ removed from ES6)  
> The value of the VariableEnvironment component never changes while the value of the LexicalEnvironment component may change during execution of code within an execution context.

---

## (ES12- , 2021- )
In ES12 the concept of `lexical environments` is replaced with `Environment Records` model.

### 9.1 Environment Records
> - `Environment Record` is a specification type used to define the association of Identifiers to specific variables and functions, based upon the lexical nesting structure of ECMAScript code.  
> - Every Environment Record has an [[OuterEnv]] field, which is either null or a reference to an outer `Environment Record`.

### 9.1.1 The Environment Record Type Hierarchy
> - Environment Records can be thought of as existing in a simple object-oriented hierarchy where Environment Record is an abstract class with `three` concrete subclasses: **declarative Environment Record**, **object Environment Record**, and **global Environment Record**.  
> - Function Environment Records and module Environment Records are subclasses of declarative Environment Record.

### 9.3 Execution Contexts
> Table 25: Additional State Components for ECMAScript Code Execution Contexts  
> - **LexicalEnvironment**: Identifies the `Environment Record` used to resolve identifier references made by code within this execution context.  
> - **VariableEnvironment**: Identifies the `Environment Record` that holds bindings created by VariableStatements within this execution context.

> The **LexicalEnvironment** and **VariableEnvironment** components of an execution context are always `Environment Records`.
