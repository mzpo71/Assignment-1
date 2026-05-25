# Why is "any" labeled a "type safety hole," and why is "unknown" the safer choice for handling unpredictable data? Explain the concept of type narrowing.

The main goal for using typescript to make code type-safe so that expected errors can be avoided . However many people use "any" which becomes security concern.Using "any" cause typescript to lose its type-checking capabilities.That's why it is known as "type safety hole"  . on the other side "unknown" is not alsp flexible but also secured . In this blog I'll discuss about "any" , "unknown and type-narrowing .

## Why using any is labeled as "type safety hole"

If "any" is used , then typescript compiler skips type-checking which results . The compiler allows any operation even if it is invalid .
 
 ```typescript
 let x:any = "Hello world!" ;
 console.log(x.toUpperCase()) ; // it will work
 x = 2026 ;
 console.log(x.toUpperCase()) ; // It will cause runtime error. But compiler will not warn you .
 ```

after using any the compiler does not give any warning.This is the problem with any.and this is why is labeled "type safety hole" . 

## Why "unknown" is a better option 

"unknown" type also can contain any value . However it will force to check the data type . 

```typescript
let x:unknown = "Hello World!"

if(typeof x ==="string"){
    console.log(x.toUpperCase()) ; 
}

```
This is how "unknown" does not let coders do any operation . 

## What is type narrowing
 Type narrowing is a process where typescript refine a broad type to a more specific type. It can be done by condition checks

 ```typescript
function givenInput(x: unknown):string{
    if (typeof x === "string"){
        console.log(x.toUpperCase()) ; 
    }
    else if (typeof x === "number"){
        console.log(x+10) ;
    }
    else {
        return "invalid" ;
    }
}
 ```

 Using "any" cancels the security benefits of typescript. Unknown ensures type-safety by forcing coder to check data type and do type-narrowing 
