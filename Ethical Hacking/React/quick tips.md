
```css

.profileScreen__details > h2{

    background-color: gray;

    padding: 15px;

    font-size: 15px;

    padding-left: 20px;

}
```


this used for navigate

```js

const isProfilePage =window.location.pathname==='/profile';

 <img onClick={(isProfilePage ? null  :() => navigate("/profile"))} />
```

## this is for scroll animation

```js
const [show,handleShow] = useState(false);

 const transitionNavBar = () => {
        if(window.scrollY>100){
            handleShow(true);
        }else{
            handleShow(false);
        }
    };

    useEffect( () => {
        window.addEventListener('scroll',transitionNavBar);
        return () => window.removeEventListener('scroll',transitionNavBar);
    },[]);
    
   //👇 this for the navbar design
   
   <div className={`nav ${show && 'nav__black'}`}>
```

```css
.nav{
 transition-timing-function:ease-in ;

    transition: all 0.5s;
}
.nav__black{
background-color: black;
}


```