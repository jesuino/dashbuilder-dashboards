
jBPM DB Dashboards
--

Sample DashBuilder jBPM dashboard that retrieves data directly from the database. Useful for jBPM embedded users that does not make use of Kie Server.

The dashboard can run on DashBuilder Runtime and imported in Business Central/DashBuilder to be edited.



### Dashboard Pages

The pages from this dashboards are based on default monitoring pages from Business Central:

* **Process Reports**: Responsible to show a summary of all processes

![image](https://user-images.githubusercontent.com/359820/128437522-b093c433-556d-4741-90a7-0519965ff94c.png)

* **Task Reports**: Responsible to show a summary of all human tasks.

![image](https://user-images.githubusercontent.com/359820/128437449-bf9b85ce-1d8f-4f4c-856e-634f4fdbf394.png)


### Setup

These dashboards make use of [SQL datasets and](https://blog.kie.org/2021/07/add-sql-datasource-for-authoring-dashboards.html) they consult a datasource with JNDI name equals to _java:jboss/datasources/jbpmdb_ to access the jBPM database. For more information about SQL data sets check [this post](https://blog.kie.org/2021/07/add-sql-datasource-for-authoring-dashboards.html). Here's a sample MariaDB datasource for Wildfly 19:

```
<datasource jndi-name="java:jboss/datasources/jbpmdb" pool-name="jbpmdb" enabled="true" use-java-context="true">
        <connection-url>jdbc:mariadb://localhost:3306/jbpmdb</connection-url>
    <driver>mariadb</driver>
    <security>
        <user-name>jbpm</user-name>
        <password>jbpm</password>
    </security>
</datasource>
```

Notice that you can either import the dashboards to edit it on Business Central or just run it on DashBuilder Runtime. If you decide yo use Dashbuilder Runtime Quarkus distribution you must setup SQL datasource using the following system properties:

```
java \
-Ddashbuilder.datasources=jbpmdb \
-Ddashbuilder.datasource.jbpmdb.jdbcUrl=jdbc:mariadb://localhost:3306/jbpmdb \
-Ddashbuilder.datasource.jbpmdb.providerClassName=org.mariadb.jdbc.Driver \
-Ddashbuilder.datasource.jbpmdb.maxSize=10 \
-Ddashbuilder.datasource.jbpmdb.principal=jbpm \
-Ddashbuilder.datasource.jbpmdb.credential=jbpm \
-jar dashbuilder-runtime-app-8.0.0-alpha.jar
```

Once the datasource setup is ready, just import the [jBPM Dashboard](https://github.com/jesuino/dashbuilder-dashboards/blob/main/jBPM%20DB%20Dashboard/jbpm_reports.zip) zip file on your installation using [Content Transfer](https://access.redhat.com/documentation/en-us/red_hat_process_automation_manager/7.5/html/configuring_business_central_settings_and_properties/exporting-importing-dashbuilder-data-proc-configuring-central) or importing into [DashBuilder](https://blog.kie.org/2020/09/introducing-dashbuilder-runtime.html).

