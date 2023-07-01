```js

const obj={
name:'harish',
age:20,
glob(){                          ✔️
console.log("hello");
},
greating : function(){           ✔️
console.log("again Hello" + this.name);
},
const great=()=> {
console.log("alrigt " + this.name); ❌ // in arrow functions we cant                                           //use this because it does not search items does not inside of the function
}
}
```


![[Pasted image 20230623013642.png]]  

![[Pasted image 20230623205545.png]]  
