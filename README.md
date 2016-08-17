# DBus Java Helper 

## Installing `dbus-java`

Required java dependencies for dbus java bindings:
- `dbus.jar`
- `hexdump.jar`
- `unix.jar`

### Installing from repository
To get required dependencies, just install them from repository:
```bash
sudo apt-get update
sudo apt-get install libdbus-java
```

### Installing from source code
`Hexdump.jar` and `unix.jar` are part of `libmatthew-java library`, available on site: http://www.matthew.ath.cx/projects/java/.
To download, build and install execute following bash commands:
```bash
wget http://www.matthew.ath.cx/projects/java/libmatthew-java-0.8.tar.gz
tar -xzf libmattew-java-0.8.tar.gz
cd libmatthew-java-0.8/
make
sudo make install
```
If error with `jni.h` will appear, then `JAVA_HOME` variable is not set.

Dbus-java source code is avaiable to download in site: https://dbus.freedesktop.org/doc/dbus-java/.
```bash
wget https://dbus.freedesktop.org/releases/dbus-java/dbus-java-2.7.tar.gz
cd dbus-java-2.6
```
...link `libmatthew-java` dependencies...
```bash
ln -s unix-0.2.jar unix.jar  
ln -s debug-disable-1.1.jar debug-disable.jar  
ln -s hexdump-0.1.jar hexdump.jar
```
...make and install.
```bash
make
sudo make install
```

### Preparing project
After instalation, libraries should be located in `/usr/share/java`. To add them into maven run:
```bash
mvn install:install-file -Dfile="/usr/share/java/dbus.jar" -DgroupId=org.freedesktop.dbus -DartifactId=dbus-java -Dversion=2.7.0 -Dpackaging=jar
mvn install:install-file -Dfile="/usr/share/java/unix.jar" -DgroupId=cx.ath.matthew -DartifactId=unix -Dversion=0.5.0 -Dpackaging=jar
mvn install:install-file -Dfile="/usr/share/java/hexdump.jar" -DgroupId=cx.ath.matthew -DartifactId=hexdump -Dversion=0.2.0 -Dpackaging=jar
```
Finally add to java library path place where `libunix-java.so` is located by running application with param:
`-Djava.library.path=/usr/lib/jni`.
