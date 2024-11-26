## JNI Example
This is a simple example of how to use JNI to call a C function from Java.

### Compile the Java file
```bash
javac HelloWorldJNI.java
```

### Generate the header file
```bash 
javac -h . HelloWorldJNI.java
```

### Generate the shared library for Linux OS
```bash
gcc -shared -o libhelloworld.so -fPIC HelloWorldJNI.c -I"$JAVA_HOME/include" -I"$JAVA_HOME/include/linux"
```

### Generate the shared library for Mac OS
```bash
gcc -shared -o libhelloworld.dylib -fPIC HelloWorldJNI.c -I"$JAVA_HOME/include" -I"$JAVA_HOME/include/darwin"
```
```bash
ls /Library/Java/JavaVirtualMachines/jdk-17.jdk/Contents/Home/include/darwin/jni_md.h\n
```

### Generate the shared library for Windows OS
```bash
gcc -shared -o helloworld.dll -fPIC HelloWorldJNI.c -I"$JAVA_HOME/include" -I"$JAVA_HOME/include/win32"
```

### Run the Java program
```bash
java -Djava.library.path=. HelloWorldJNI
```