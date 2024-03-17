# express.js development, how can we auto-reload back-end & front-end without refreshing browser & restarting express server manually?



## project init

```
express --ejs --css=sass --git demo
cd demo
npm i

// package.json, add "dev"
"scripts": {
	"dev-original": "SET DEBUG=demo:* & npm start"
}
```



```
// app.js
// change sass to scss

app.use(sassMiddleware({
	indentedSyntax: false
}))
```



### watching front-end

```
npm i -D livereload

// app.js
const liveReloadServer = require('livereload').createServer()

const publicDir = path.join(__dirname, "public")
liveReloadServer.watch(publicDir)
liveReloadServer.server.once("connection", () => {
	setTimeout(() => {
		liverReloadServer.refresh("/")
	}, 100)
})
```

```
npm i -D connect-livereload

// app.js
const connectLiveReload = require('connect-livereload')

app.use(connectLiveReload())
```

### watching back-end

```
npm i -D nodemon

// package.json
"scripts": {
	"start": "node ./bin/www",
	"dev-original": "SET DEBUG=demo:* & npm start",
	"dev": "nodemon --ext js,ejs,scss"
}
```

### run

```
npm run dev
```

