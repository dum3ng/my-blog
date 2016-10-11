##try
When using a function throws some exception, you should process the error either in a `do-catch` block or use `try?` or `try!` to make a type cast.

    do {
        var a = someThrowFunction()
    } catch {
        print("error occured")
    }
or 
    
    //will create an optional
    var a = try? someThrowFunction()
    
    //will cause a runtime error if exception throwed
    var b = try! someThrowFunction()
    
##as
Although the `as` has the same typing with its permutation keywords `as?` and `as!`, in fact they does different works.
In type checking and downcasting, `is` is in the same group with `as?` and `as!`.

###is
Use `is` to check if an object is an instance of a class or its subclasses.

###as
Used when upcasting.
i.e. 

    String as Any
###as? and as!
Downcasting maybe failed, so using `as?` to get an optional value.
And use `as!` when you are sure the downcasting will succeed.



