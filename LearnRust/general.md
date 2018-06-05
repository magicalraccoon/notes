Keywords Currently in Use

    as - primitive casting, disambiguating the specific trait containing an item, or renaming items in use and extern crate statements
    break - exit a loop immediately
    const - constant items and constant raw pointers
    continue - continue to the next loop iteration
    crate - external crate linkage or a macro variable representing the crate in which the macro is defined
    else - fallback for if and if let control flow constructs
    enum - defining an enumeration
    extern - external crate, function, and variable linkage
    false - Boolean false literal
    fn - function definition and function pointer type
    for - iterator loop, part of trait impl syntax, and higher-ranked lifetime syntax
    if - conditional branching
    impl - inherent and trait implementation block
    in - part of for loop syntax
    let - variable binding
    loop - unconditional, infinite loop
    match - pattern matching
    mod - module declaration
    move - makes a closure take ownership of all its captures
    mut - denotes mutability in references, raw pointers, and pattern bindings
    pub - denotes public visibility in struct fields, impl blocks, and modules
    ref - by-reference binding
    return - return from function
    Self - type alias for the type implementing a trait
    self - method subject or current module
    static - global variable or lifetime lasting the entire program execution
    struct - structure definition
    super - parent module of the current module
    trait - trait definition
    true - Boolean true literal
    type - type alias and associated type definition
    unsafe - denotes unsafe code, functions, traits, and implementations
    use - import symbols into scope
    where - type constraint clauses
    while - conditional loop



Debug should format the output in a programmer-facing, debugging context.
Federated timeline
Display is similar to Debug, but Display is for user-facing output, and so cannot be derived.

"Dangling pointer" = a pointer that references a location in memory that may have been given to someone else

slices do not have ownership

enumerate wraps the result of iter and returns each element as part of a tuple instead.

these mean the same thing:
    let slice = &s[0..len];
    let slice = &s[..];

Rust doesn’t allow us to mark only certain fields as mutable.

Each struct we define is its own type, even though the fields within the struct have the same types

We can also define structs that don’t have any fields! These are called unit-like structs

However, methods are different from functions in that they’re defined within the context of a struct (or an enum or a trait object) and their first parameter is always self, which represents the instance of the struct the method is being called on.

 Methods can take ownership of self, borrow self immutably as we’ve done here, or borrow self mutably, just like any other parameter.

reading (&self), mutating (&mut self), or consuming (self)

Structs let us create custom types

There’s another advantage to using an enum rather than a struct: each variant can have different types and amounts of associated data.

 you can put any kind of data inside an enum variant: strings, numeric types, or structs, for example. You can even include another enum!

Option, which is another enum defined by the standard library.

An enum in Rust is a (single) type that represents data that is one of several possible variants.

Matches in Rust are exhaustive: we must exhaust every last possibility in order for the code to be valid.

The _ pattern will match any value.
