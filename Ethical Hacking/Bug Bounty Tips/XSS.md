```js
Bug Bounty Tip 
When testing for XSS, consider where you inject your payload.
1) Before the original value
2) After the original value 
3) Replacing the original value 

Sometimes the payload will work only if added to the end (or beginning) of the original value.
Cheers!
```
