##use `is` 
    
    var three:Int = 3
    if three is Int {
    
    }
    
##use Mirror struct
    
    var s = "hello"
    let mirror = Mirror(reflecting:s)
    if mirror.subjectType == String.self {
    
    }
## use as
Use `as?` to get an optional value contains the original value and  `as!` to enforce wrap the value the target type.
    
The `as` can be used in `switch` statement to check the type.
    