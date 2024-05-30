```js
const BASE_ENDPOINT = "https://api.openweathermap.org/data/2.5/";

const API_KEY = 'aeb34d2e1bfdfb9056cefc713e2b2a37';

  

const city = "Edmonton";

const currentWeatherEndpoint = `${BASE_ENDPOINT}weather?q=${city}&appid=${API_KEY}`;

  

fetch(currentWeatherEndpoint)

    .then((res)=> res.json())

    .then((data) => {

        console.log(data);

    });
```

```python
print("Hello Kulraj")
```



