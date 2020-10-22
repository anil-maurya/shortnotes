# Async JavaScript


Code which can start now and finishes later



## Promise

Create new promise

```js

const getSomething = () =>{

new Promise((resolve, reject)=>{
	resolve('Somedata');

});

};


getSomething()
	.then(data=>console.log(data))
	.catch(err=>console.log(err))


///

````

## Aynchronous JavaScript (aysnc/await)


```js

// async always return promises

const getTodos = aysnc () =>{
	const response = await featch('todo/something.json');
}

````

