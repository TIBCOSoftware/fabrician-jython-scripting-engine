[fabrician.org](http://fabrician.org/)
==========================================================================
Jython Scripting Engine Guide
==========================================================================

Introduction
--------------------------------------
This project builds a Jython grid library for use in creating Silver Fabric Enabler scripts in Jython.  The
Silver Fabric Broker already contains a version of Jython but this project provides a way to get the latest
and greatest or an alternate version if needed.

Examples
--------------------------------------

Installation
--------------------------------------
To build the grid library, you must have Maven installed and set in your path. Then, run the
following:

```bash
  mvn install
```

If successful, the grid library will be created and uploaded to a running Broker.


Examples
--------------------------------------
Jython script examples for use in Silver Fabric Component and Enablers can be found in the [wiki](https://github.com/fabrician/jython-scripting-engine/wiki).

To use Jython for a Silver Fabric, make sure your "language" and "languageVersion" 
properties in the domain.xml or container.xml correspond the library you built:

```xml
    <script class="com.datasynapse.fabric.common.script.Script">
        <property name="name" value="enabler.py"/>
        <property name="language" value="python"/>
        <property name="languageVersion" value="2.5"/>
    </script>
```
