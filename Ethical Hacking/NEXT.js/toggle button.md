
```js

const [show,setShow] = useState(false);


{show ? <h1>Hello<h1/> : null}

<button onClick={() => setShow(!show)} >Toggle <button/>
```