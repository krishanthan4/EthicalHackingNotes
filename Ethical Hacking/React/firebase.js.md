👇this is the new template for firebase configuration

```js

import firebase from 'firebase/compat/app';
import 'firebase/compat/auth';
import 'firebase/compat/firestore';

const firebaseConfig = {
    apiKey: "AIzaSyCuw3oFY7JbzOLb1fVY0LBkcuQEf-DMfdQ",
    authDomain: "netflix-clone-22a89.firebaseapp.com",
    projectId: "netflix-clone-22a89",
    storageBucket: "netflix-clone-22a89.appspot.com",
    messagingSenderId: "1094347326950",
    appId: "1:1094347326950:web:ff0732cec9d7ab391a0227"
  };

// Use this to initialize the firebase App
const firebaseApp = firebase.initializeApp(firebaseConfig);

// Use these for db & auth
const db = firebaseApp.firestore();
const auth = firebase.auth();

export { auth, db };
```


