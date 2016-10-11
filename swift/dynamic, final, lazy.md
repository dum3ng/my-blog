>dynamic
Apply this modifier to any member of a class that can be represented by Objective-C. When you mark a member declaration with the dynamic modifier, access to that member is always dynamically dispatched using the Objective-C runtime. Access to that member is never inlined or devirtualized by the compiler.

>Because declarations marked with the dynamic modifier are dispatched using the Objective-C runtime, they’re implicitly marked with the objc attribute.



摘录来自: Apple Inc. “The Swift Programming Language (Swift 3)”。 iBooks. 

##final
class: will not be subclassed.
method: will not be overrided.
variable: will not be changed in subclasses.



##lazy
The variable with a lazy declaration prefix will be evaluted only when it is first time accessed.