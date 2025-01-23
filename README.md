# FRONT-END INTERVIEW QUESTIONS :cowboy_hat_face:
There are some questions and answers which are asked repeatedly in various interviews. So, this is the best place to go through and revise things before going to attend any front-end interviews.
**Note: -** Please do not rely on these questions only, as mentioned above these are the pre-interview revision questions.
## JavaScript
### Differences between var, let and const? Output questions using var and const.
**Differences between var, let, and const**
1. **Scope:**
   - **var:** Function-scoped.
   - **let and const:** Block-scoped.
2. **Hoisting:**
   - **var:** Hoisted to the top of its scope and initialized with undefined.
   - **let and const:** Hoisted but not initialized.
3. **Reassignment:**
   - **var and let:** Can be reassigned.
   - **const:** Cannot be reassigned.
4. **Redeclaration:**
   - **var:** Can be redeclared within the same scope.
   - **let and const:** Cannot be redeclared within the same scope.

**Examples**
```
Using var:
function varExample() {
    console.log(x); // undefined (due to hoisting)
    var x = 10;
    console.log(x); // 10
}
varExample();
```
```
Using const:
function constExample() {
    const y = 20;
    console.log(y); // 20
    // y = 30; // Error: Assignment to constant variable.
}
constExample();
```
