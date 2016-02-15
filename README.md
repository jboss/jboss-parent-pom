JBoss Parent POM
=================
The parent Maven POM for JBoss community projects.

What is it?
-----------
The JBoss parent POM provides default configuration for Maven builds.
 
* Recommended/Default versions for the most commonly used Maven plugins
* Manifest configuration for the jar and assembly plugins
* Profiles for generating source jars, and enforcing a minimum versions of 
  Java and Maven
* Distribution Management and other configuration for deploying to the 
  JBoss.org Maven repositories

How to use it?
--------------
Start out by adding the parent configuration to your pom.

    <parent>
      <groupId>org.jboss</groupId>
      <artifactId>jboss-parent</artifactId>
      <version>20</version>
    </parent>

The pom includes properties which allow various build configuration to be 
customized.  For example, to override the default version of the
maven-compiler-plugin, just set a property.

    <properties>
      <version.compiler.plugin>3.1</version.compiler.plugin>
    </properties>

Or override the default Java compiler source and target level used in the build.  
Note the default level is 1.8.

    <properties>
      <maven.compiler.target>1.7</maven.compiler.target>
      <maven.compiler.source>1.7</maven.compiler.source>
    </properties>

The minimum version of Java or Maven required to run a build can also be set via
properties.

    <properties>
      <maven.min.version>3.0.3</maven.min.version>
      <jdk.min.version>1.7</jdk.min.version>
    </properties>

If jdk.min.version is not set, it default to version defined by maven.compiler.source

For the full list of properties, refer to the POM itself.


The JBoss Release Profile
--------------------
The parent POM includes a Maven profile called "jboss-release".  This profile contains 
settings for generating a full project source archive, javadoc jar files, and
release deployment metadata.  If using the Maven release plugin, this profile
will automatically be activate during the release:perform step.

If the Maven release plugin is not used during the release process, the profile
can be manually activated from the command line during a release build.

    mvn -Pjboss-release deploy


The GPG Sign Profile
--------------------
This POM includes a Maven profile called "gpg-sign" which provides default 
configuration to generate GPG signatures for the build artifacts.  

    mvn -Pgpg-sign deploy

In order for the gpg plugin to properly create a signature for each artifact,
the properties "gpg.keyname" and "gpg.passphrase" must be available to 
the current build.  These properties can either be set in a
build profile, or on the command line.

    <profile>
      <id>gpg-config</id>
      <properties>
        <gpg.keyname>me@home.com</gpg.keyname>
        <!-- Don't keep passphrase in plain text! -->
        <gpg.passphrase>secret</gpg.passphrase>
      </properties>
    </profile>


Where to get more information?
---------------------------------
The [github wiki](https://github.com/jboss/jboss-parent-pom/wiki) provides some 
additional examples.  For questions/suggestions about the jboss-parent-pom, 
head to the [JBoss Community Build space](http://community.jboss.org/en/build) 
on the jboss.org site.  Issues related to the jboss-parent-pom can be submitted 
to the [JBoss build jira project](https://issues.jboss.org/browse/JBBUILD)

License
-------
* This software is in the public domain

