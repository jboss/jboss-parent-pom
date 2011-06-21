JBoss Parent POM
================
The parent POM for JBoss community projects.

What is it?
-----------
The JBoss parent POM provides default configuration for JBoss Maven builds.
 
* Default versions for the most commonly used Maven plugins
* Manifest configuration for the jar and assembly plugins
* Profiles for generating source jars, and enforcing a minimum Maven version
* Distribution Management and other required configuration for deploying to the JBoss.org Maven repositories

How to use it?
--------------
Start out by adding the parent configuration to your pom.

    <parent>
      <groupId>org.jboss</groupId>
      <artifactId>jboss-parent</artifactId>
      <version>6-beta-2</version>
    </parent>

Depending on the needs of your build, you can customize the plugins and other settings using properties.
For example, to override the default version of the maven-compiler-plugin, just set a property.

    <properties>
      <version.compiler.plugin>2.3</version.compiler.plugin>
    </properties>

Or override the default Java compiler source and target level used in the build.  Note the default level is 1.6.

    <properties>
      <maven.compiler.target>1.5</maven.compiler.target>
      <maven.compiler.source>1.5</maven.compiler.source>
    </properties>

For the full list of properties, refer to the POM itself.

Where can I get more information?
---------------------------------
The [https://github.com/jboss/jboss-parent-pom/wiki](github wiki) provides some additional examples.
For questions/suggestions about the jboss-parent-pom, head to the [http://community.jboss.org/en/build](JBoss Community Build space) on the jboss.org site.
Issues related to the jboss-parent-pom can be submitted to the [https://issues.jboss.org/browse/JBBUILD](JBoss build jira project)

License
-------
* [GNU Lesser General Public License Version 2.1](http://www.gnu.org/licenses/lgpl-2.1-standalone.html)

