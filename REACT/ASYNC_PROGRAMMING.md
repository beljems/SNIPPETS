# ASYNC PROGRAMMING

```sh
LOUPE JS PLAYGROUND
[http://latentflip.com/loupe/](http://latentflip.com/loupe/)
To check running functions hierarchy

```sh
Synchonous - one at a time
Asynchronous - at the same time```

## ASYNC PROGRAMMING
[http://latentflip.com/loupe/](http://latentflip.com/loupe/)

```sh
console.log('start'); // first call

setTimeout(() => {
  console.log('async call');
});

// last call

console.log('end'); // second call```

### Promise is async method
```let promise = new Promise((resolve, reject) => {
  let error = false;
  if(error) {
    reject('Error');
  } else {
    resolve(1);
  }
})

promise.then((res) => {
  console.log(res);
  console.log('done');
}, (err) => {
  console.log(err);
})```

### Promise with $.ajax
```sh
let promise = $.ajax('https://');

promise.then((res) => {
  console.log(res);
  console.log('done');
}, (err) => {
  console.log(err);
})```

## ES8/EcmaScript 2017
```sh
Async - Promise
Await - .then

Example

console.log('start'); // first call

let res = await // second call

console.log('end'); // third call```

### ASYNC
```sh
async function main() {
  console.log('start');

  // or .then
  let result = await getPromise();
  console.log(result);
  console.log('end');
}```

### PROMISE THEN
```sh
async function main() {
  console.log('start');

  let result = getPromise();

  promise.then((result) => {
    console.log(result);
    console.log('end');
  })
}

main();

async function getPromise() {
  return new Promise((resolve, reject) => {
    let error = false;
    if(error) {
      reject('Error');
    } else {
      resolve(1);
    }
  })

}```

## AXIOS
- visit axios site
```sh const axios = require('axios');

axios.get('https://reqres.in/api/users')
.then((res) => {
  console.log(res);
  console.log('done');
});

ASYNC/Await in Axios
import Axios from 'axios';```

### GET
```sh
async function main() {
  console.log('start');
  let result = await axios.get('https://reqres.in/api/users', {

  })
  console.log(result.data);
  console.log('end');
})

main();```

### POST
```sh
async function main() {
  console.log('start');
  let result = await axios.post('https://reqres.in/api/users', {

  })
  console.log(result.data);
  console.log('end');
})

main();```

### HTTPS METHOD
```sh
async function main() {
  console.log('start');
  let result = await axios({
     method: 'POST',
     url: 'https://reqres.in/api/users',
     data: {
       email: EMAIL_HERE
     }    
  })
  console.log(result.data);
  console.log('end');
})
main();```

### PATCH
```sh
async function main() {
  console.log('start');
  let result = await axios({
     method: 'PATCH',
     url: 'https://reqres.in/api/users/2',
     data: {
       email: EMAIL_HERE
     },
     header: {
       Authorization: KEY_HERE
     }   
  })
  console.log(result.data);
  console.log('end');
})
main();```

## REST
visit rest api, below are basics

http methods
```sh
get - /users - list all users
    - /users/id - get resource with id
post
    - /users - create/insert a resource
put
    - /users/id - update resource (complete)
      with firstname, lastname
patch
    - /users/id - update resource (incomplete)
      need user with lastname
delete
    - /users/id - delete resource
```
