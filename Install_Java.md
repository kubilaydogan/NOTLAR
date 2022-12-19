# How to Install Java on MacOS?

1) Download Java from the [Oracle website](https://www.oracle.com/java/technologies/downloads/#jdk17-mac) and install it.

2) Set JAVA_HOME variable

```bash
echo export "JAVA_HOME=\$(/usr/libexec/java_home)" >> ~/.zshrc
```
<img src="img/nano.png" width=500></img>

```bash
$ source ~/.zshrc
 
$ echo $JAVA_HOME (to verify path)
```


