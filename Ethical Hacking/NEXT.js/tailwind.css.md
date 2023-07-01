
```css
tracking-[15px]  👈 for letter spacing
tracking-widest
```
![[Pasted image 20230613192516.png]]

👇this style 👇
```css
@layer components {

  .heroButton{

    @apply px-6 py-2 border border-[#242424] rounded-full uppercase text-sm text-gray-500 transition-all tracking-widest hover:border-[#F7AB0A]/40 hover:text-[#F7AB0A]/40

  }

}
```

object-fit 👈 this class uses for keep the images aspect ratio in same.

  flex-shrink-3  👈 this can shrink the col/row of a flex
![[Pasted image 20230614115505.png]]  
```css
 bg-[#F7AB0A]/10  👈 for put the color with a opacity
```

```css
-skew-y-12  👈  for turn round like this 👇
```

![[Pasted image 20230614142636.png]]  


```cs

   viewport={{

                once:true,

            }}
            
👆//this is for render the animation once
```
