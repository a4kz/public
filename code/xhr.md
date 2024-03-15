### XMLHttpRequest Obj
```
// windows
const createXHR = () => {
	let versions = [
		'Microsoft.XMLHttp',
		'MSXML2.XMLHttp',
		'MSXML2.XMLHttp.3.0',
		'MSXML2.XMLHttp.4.0',
		'MSXML2.XMLHttp.5.0',
		'MSXML2.XMLHttp.6.0'
	]
	
	for (let i = 0; i < versions.length; i++) {
		try {
			const xhr = new ActiveXObject('Microsoft.XMLHttp')
			return xhr
		} catch (err) {
			// error handler
			throw new Error('MSXML is not installed.')
		}
	}
}
```

### XHR call
```
xhr.open('GET/POST', url, async)
```

- request type: `GET` | `POST`
- url：请求的地址
- async：
	- true，异步请求；
	- false，同步请求

### `onreadystatechange` event handler
### `xhr.readyState`
- `0`: xhr对象以创建，但是还没有调用`open()`
- `1`: 加载中，`open()`没有调用，但是请求还没有发
- `2`: 已加载，请求已发送
- `3`: 交互中，已经收到部分相应
- `4`: 请求已完成，已经接受到所有数据，连接已关闭

### send`GET` request
```
const xhr = new XMLHttpRequest()
xhr.open('GET', '/got/info', true)
xhr.onreadystatechange = () => {
	// 此处不要用this.readyState
	if (xhr.readyState == 4) {
		if (xhr.status == 200 || xhr.status == 304 ) {
		// ... do something ...
		alert('Got response')
		}
	}
}
xhr.setRequestHeader('key', 'value')
xhr.send(null)
```

- `xhr.responseText`
- `xhr.responseXML`
- `xhr.status`
- `xhr.statusText`

### send`POST`request
```
const xhr = new XMLHttpRequest()
xhr.open('POST', url, true)
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')

xhr.onreadystatechange = () => {
	if (xhr.readyState == 4) {
		if (xhr.status == 200 || xhr.status == 304) {
			
		} else {
		
		}
	}
}

let conent = "key1=val1&key2=val2&key3=val3"
xhr.send(content)
```

### `xhr.getResponseHeader('Content-Type')`
- `text/xml`
- `text/html`
- `text/plain`

```
const strHeaders = xhr.getAllResponseHeaders()
const arrHeaders = headers.split(/\r?\n/)

for (let i = 0; i < arrHeaders.length; i++) {
	console.log(arrHeaders[i])
}
```

```
xhr.setRequestHeader(key, value)
```