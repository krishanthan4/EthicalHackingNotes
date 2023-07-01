![[Pasted image 20230602201336.png]]  

## Redux is build with functional programming so let's dive in to it.


In javascript we can assign a function for a variable 

![[Pasted image 20230602201814.png]]  

a function can call from another function

![[Pasted image 20230602201934.png]]  

## Higher order function

higher order function means a function inside a function

map,
![[Pasted image 20230602202504.png]]  
setTimeOut ,
![[Pasted image 20230602202447.png]]  
are higher order functions 


reusable functions( functional composition )

![[Pasted image 20230602203405.png]]  


## immutability

here have a array :

### const person = [name:'John'] ;

now ,we want to update the name ,so first we want to get a copy of the array.and update it in it.

const updated = {
...person , {
name:'Bob';
},
}

![[Pasted image 20230602210007.png]]  

## To update a array 

update a number front of a array 👇

![[Pasted image 20230602210138.png]]  

update a number end of a array 👇

const added = [...number , 4];

in redux there are mainly 3 parts


![[Pasted image 20230602213028.png]]  


## installing redux

npm i redux@4.0

## Designing the Store 

Creating the reducer

reducer.js

![[Pasted image 20230602215243.png]]   
![[Pasted image 20230602215205.png]]  

Creating the Store

store.js

