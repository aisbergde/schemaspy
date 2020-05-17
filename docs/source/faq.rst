.. |br| raw:: html

   <br />

Frequent Asked Questions
=========================

General
--------

Schema or Catalog name can't be null
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This means that Schema or Catalog information could not be extracted from connection. |br|
I this case you need to add options ``-s [schemaName]`` or ``-cat [catalogName]`` |br|
In most cases for catalog you can use ``-cat %`` |br|
In mysql you can use same as ``-db`` |br|

"Cannot enlarge memory arrays" when using viz.js
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
According to viz.js documentation the memory is default 16MB this should be enough. |br|
We have increased this to 64 MB if you receive this error, please report this to us. |br|

I just receive a cryptic error like "ERROR - null"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The code has previously avoided to log stracktraces, we now log them but only when |br|
``-debug`` is used. So any cryptic error can be enhanced with stacktrace by running |br|
SchemaSpy with the argument ``-debug`` |br|

OSX
----

Graphviz
~~~~~~~~~
There have been lots of issue with graphviz and OSX |br|
So install using brew ``brew install graphviz --with-librsvg --with-pango`` |br|
Depending on OSX version |br|
*Older than High Sierra*, add ``-renderer :quartz`` to the commandline |br|
*High Sierra or newer*, add ``-renderer :cairo`` to the commandline |br|

I am using SQL Server an not all Routines (Procedures, Functions) are documented
~~~~~~~~~
The used user probably has too few rights. ``VIEW DEFINITION`` rights should be granted::

   --check current rights in the database you want to document
   USE AdventureWorks2017;
   GO
   sp_helprotect;

   --grant VIEW Definition Rights in a specific database
   USE AdventureWorks2017;
   GO
   GRANT VIEW DEFINITION TO User1;

   --OR grant VIEW Definition Rights in all databases
   USE master;
   GO
   GRANT VIEW ANY DEFINITION TO User1;

   --turn off the additional rights to VIEW Definition in all databases
   USE master;
   GO
   REVOKE VIEW ANY DEFINITION TO User1;

   --turn off the additional rights to VIEW Definition i a specific database
   USE AdventureWorks2017;
   GO
   REVOKE VIEW DEFINITION TO User1;
