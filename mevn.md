# MongoDB / Express.js / Vue.js / Node.js
### NodeJS
```
// ubuntu server
$ wget https://https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-x64.tar.xz
$ VERSION=v10.16.3
$ DISTRO=linux-x64
$ sudo mkdir -p /usr/local/lib/nodejs
$ sudo tar -xJvf node-$VERSION-$DISTRO.tar.xz -C /usr/local/lib/nodejs

// add to $PATH
# NodeJS
VERSION=v10.16.3
DISTRO=linux-x64
export PATH=/usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin:$PATH

// refresh profile
$ .~/.profile

// to create a sudo link
$ sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/node /usr/bin/node
$ sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/npm /usr/bin/npm
$ sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/npx /usr/bin/npx
```

### MongoDB
```
$ wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
$ echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
$ sudo apt-get update
$ sudo apt-get install -y mongodb-org
```

Although you can specify any available version of MongoDB, apt-get will upgrade the packages when a newer version becomes available. To prevent unintended upgrades, you can pin the package at the currently installed version:

```
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```

```
// data dir
/var/lib/mongodb
```

```
// log dir
/var/log/mongodb
```

```
// config dir
/etc/mongod.conf
```

```
// start/stop mongodb
$ sudo service mongod start
$ sudo service mongod stop
```

```
// mongodb shell
$ mongo // 必须先启动服务器
```

```
// uninstall mongodb
$ sudo service mongod stop
$ sudo apt-get purge mongodb-org*
$ sudo rm -r /var/log/mongodb
$ sudo rm -r /var/lib/mongodb
```


### Express.JS
```
$ npm install -g express-generator
$ express --view=pug myapp && cd myapp
$ npm i
$ npm start 
```

```
// or
$ nodemon app
```

### Mongoose
```
$ npm i mongoose
```

### Vue.JS
```
$ npm i -g @vue/cli 
$ vue create myapp
```

```
// installing plugins in an existing project
$ vue add cli-plugin-elementui
```



