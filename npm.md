### npm permission errors

To minimize the  chance of permissions errors, you can configure npm to use a different  directory. In this example, you will create and use hidden directory in  your home directory.

1. Back up your computer.
2. On the command line, in your home directory, create a directory for global installations:

```
mkdir ~/.npm-global
```

3. Configure npm to use the new directory path:

```
npm config set prefix '~/.npm-global'
```

4. In your preferred text editor, open or create a `~/.profile` file and add this line:

```
export PATH=~/.npm-global/bin:$PATH
```

5. On the command line, update your system variables:

   ```
   source ~/.profile
   ```

6.To test your new configuration, install a package globally without using `sudo`:

```
npm install -g jshint
```

 Instead of steps 2-4, you can use the corresponding ENV variable (e.g. if you don't want to modify `~/.profile`):

```
NPM_CONFIG_PREFIX=~/.npm-global
```