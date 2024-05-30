1. Run Termninal
2. npm init -y (package.json files now added)
3. npm i -D parcel
4. npm i bootstrap
5. Edit package.json file from 
```javascript
 "scripts": {

    "test": "echo \"Error: no test specified\" && exit 1"

  },
```

to 
```javascript
 "scripts": {

    "dev": "npx parcel",

    "build": "npx parcel build"

  },
```
6. In package.json file change `"main": "index.js"` to `"source": "index.html"`
7. npm run dev
8. Put this in your `MAIN.js` file:
```js
	import 'bootstrap/dist/css/bootstrap.min.css'
```