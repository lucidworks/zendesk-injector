ZenDesk Injector
================

Injects ZenDesk Tickets into either Solr 4.x, or Lucid Apollo indexing pipeline, AKA LucidWorks 5

## Building

This project assumes Java 7 (aka Java 1.7)

If you were given a pre-built .jar file, skip to the section **Running**

To checkout and build the project you'll also need git and maven.  Issue the command:

```mvn package```

It will create a convenient **SELF CONTAINED** jar file at ```target/zendesk-injector-1.0-SNAPSHOT.jar```

Henceforth we'll refer to this as just **injector.jar**, but substitie the full path and name of the file you created.

## Running

### injector.jar

In the following examples we refer to **injector.jar**, but the actual file you have might be called something like ```zendesk-injector-1.0-SNAPSHOT.jar```; use that full name wherever we say injector.jar.  Also, if the jar file isn't in your current directory, you should include the full file path.

The jar is self contained, including all other project dependency libraries including SolrJ, and is a little over 30 megabytes in size.

### Two Ways to Run

The jar was built to be used with the ```java -jar``` convention.  Since there's only one class, it is set as primary.

It's also possible to use the jar in your classpath and call specific java classes directly, provided you know the full package and class name.  The main class is ```com.lucidworks.connectors.zendesk.ZenDeskTickets```

### Command Line Options

If no options are set, the injector prints out it's options.

```java -jar injector.jar```

Backslashes are shown to allow the example to continue on the next line.

Example: Feed all your tickets into Solr on on your local machine and default port:

```java -jar injector.jar \
    --zendesk yourcompany.zendesk.com --username you@yourcompany.com --password yourpassword```

Example: Feed all your tickets into Solr on a different machine:

```java -jar injector.jar 
    --zendesk yourcompany.zendesk.com --username you@yourcompany.com --password yourpassword \
    --solr http://othermachine:8983/solr```

Example: Feed all your tickets into Lucid using the default pipeline and collection **demo**:

Note: You **MUST** create the collection before running this, see Lucid doc.

```java -jar injector.jar 
    --zendesk yourcompany.zendesk.com --username you@yourcompany.com --password yourpassword \
    --apollo http://localhost:8765/lucid/api/v1/ --collection demo```


## Developer Note

The solr utils code is from https://github.com/LucidWorks/data-quality
