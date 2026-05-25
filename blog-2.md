# How do Pick and Omit utility types prevent code duplication while creating specialized "slices" of a master interface? Discuss how this keeps your code DRY (Don't Repeat Yourself).

The primary goal of using typescript is keep code safe,error-free. In big projects we need to use smaller and specialized version of a large "Master" interface . If we manually copy-paste repetitively in coding , we introduce duplicate which will directly violate the the DRY principle.

Typescript has two great solutions, which are two build in utility type ; such as : Pick and Omit . These utilities allow coder to derive "slices" or partial types from a master interface without duplicating .

## The Concept of Master Interface

Suppose we have a User interface in our application to store users' data. 

```typescript
interface User{
    id: string ;
    name : string ;
    age : number ;
    email : string ;
    isLoggedIn : boolean ;   
    bloodGroup : string ;
    grade : string ;
}

```
In many cases we will not need the entire interface. While registering user just have to input email,pasword and name . Other data will not be required .

## What is Pick Utility Type 

The Pick utility type constructs a new type by picking a specific set of properties from master interface.
Example :
Instead of declaring a new type, we can use Pick to slice out exactly what we need

```typescript
type UserProfileDisplay = Pick <User, "name"| "email" | "isLoggedIn"> ; 

const displayProfile : UserProfileDisplay={
    name : "Lionel Messi" ,
    email : "lm10@fcb.com" ,
    isLoggedIn : false  ,
} ;
```


 ## What is Omit Utility Type

 Omit utility does the oppsite of Pick. We can remove specific data by using Omit . It constructs a new type by copying all the properties from the master interface and then remove the specific keys.
Example :
```typescript
type newUserReg = Omit<User,"id" | "isLoggedIn" | "grade">
const regForm : newUserReg = {
    name : "Lionel Messi" ,
    age : 38 ,
    email : "lm10@fcb.com" ,
    bloodGroup : "football"
    } ;

```

## How this keeps code DRY

1. Single source of data : master User interface remains the ultimate authority . If we have to change any property type, we only have to update it once in the master interface.Every type derive thorough Pick or Omit will automatically inherit the update .
2. Human Error Reducton : Copying and pasting code repetitively will cause typos and type mismatches. Using utility type  lets the compiler do the rest of work and catching erros .


Pick and Omit are essential tools for keeping code clean,scalable and maintainable.By dynamically slicing the exact types we need from our master interfaces.

