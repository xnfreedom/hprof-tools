# Badoo HPROF Tools

## HPROF Deobfuscator

Hprof-deobfuscator is a tool for deobfuscating HPROF memory dump files that are created from builds obfuscated with either ProGuard or DexGuard.


![Before and after](/docs/before_and_after.png) <br><i>Before and after running hprof-deobfuscator</i>

### Building

The application can be built by executing the following Gradle command in the root of the git:

<code>
./gradlew deobfuscator:jarWithDependencies
</code>

This will create a jar file containing the application and its external dependencies in the following location:

<code>
./deobfuscator/build/libs/deobfuscator-all-1.0.jar
</code>

### Usage

After building the application you can execute it with the following command:

<code>
java -jar ./deobfuscator/build/libs/deobfuscator-all-1.0.jar \<mapping file\> \<input hprof\> \<output hprof\>
</code>

## HprofCruncher

HprofCruncher is a tool that converts HPROF memory dump files to the much more compact BMD file format. A size reduction of up to 97% can be achieved, however some data is lost in the process (including primitive fields and primitive arrays).

### Building

HprofCruncher is built by executing the following command from the command line, with the root of the git as your current directory.

<code>
./gradlew cruncher:jarWithDependencies
</code>

If the build is successful you will find the output jar file in the following location:

<code>
./cruncher/build/libs/cruncher-all-1.0.jar
</code>

### Usage

After building the application jar-file you can execute it with the following command:

<code>
java -jar ./cruncher/build/libs/cruncher-all-1.0.jar \<input hprof file\> \<output bmd file\>
</code>

## HprofDecruncher

HprofDecruncher is a tool that converts BMD files (created by HprofCruncher) back to HPROF memory dump files. Since some data is discarded when the BMD file is created not all HPROF data is recovered. However, if you have access the the<code>.jar</code>or<code>.apk</code>file of the application from which the memory dump was taken you can recover some additional data (strings used for class and field names).

### Building

HprofDecruncher is built by executing the following command from the command line, with the root of the git as your current directory.

<code>
./gradlew decruncher:jarWithDependencies
</code>

If the build is successful you will find the output jar file in the following location:

<code>
./decruncher/build/libs/decruncher-all-1.0.jar
</code>

### Usage

After building the application jar-file you can execute it with the following command:

<code>
java -jar ./decruncher/build/libs/decruncher-all-1.0.jar \<input bmd file\> \<output hprof file\> [string source 1] ... [string source n]
</code>

Where the string source input files can be either<code>.jar</code>,<code>.dex</code>or<code>.apk</code>files.

## Credits

Hprof-obfuscator, HprofCruncher and HprofDecruncher are brought to you by [Badoo Trading Limited](http://corp.badoo.com) and are released under the [MIT License](http://opensource.org/licenses/MIT).

Created by [Erik Andre](https://github.com/erikandre)


