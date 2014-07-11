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
Jython script examples for use in Silver Fabric Component and Enablers can be found in the [wiki|https://github.com/fabrician/jython-scripting-engine/wiki].

Installation
--------------------------------------
To build the grid library, you must have Maven installed and set in your path. Then, run the
following:

```bash
  mvn install
```

If successful, the grid library will be created and uploaded to a running Broker.


Example
--------------------------------------
To use Jython for a Silver Fabric, make sure your "language" and "languageVersion" 
properties in the domain.xml or container.xml correspond the library you built:

```xml
    <script class="com.datasynapse.fabric.common.script.Script">
        <property name="name" value="enabler.py"/>
        <property name="language" value="python"/>
        <property name="languageVersion" value="2.5"/>
    </script>
```
    
An example enabler script (referenced as "enabler.py" in the XML above) in Jython might look 
like the following:

```python
from java.lang import Class
from java.lang import System
from jarray import array

from com.datasynapse.fabric.admin.info import GridlibInfo

def getDynamicGridlibDependencies():
    logger.info("Adding Default Domain Type dependency")
    defaultDomainGridlib = GridlibInfo()
    defaultDomainGridlib.name = "default-domain-type"
    
    logger.info("Adding HSQLDB distribution dependency")
    hsqlGridlib = GridlibInfo()
    hsqlGridlib.name = "hsqldb1_8-distribution"
    hsqlGridlib.version = "1.0"
    
    return array([hsqlGridlib, defaultDomainGridlib], GridlibInfo)
```    
NOTE: this is not a complete Enabler implementation and only serves as an example guide to get started. Consult the Silver Fabric documentation for more information.
