
Kie Server Dashboards
--

Sample DashBuilder Kie Server dashboard that retrieves data directly from the Kie Server using advanced queries REST APU. Useful for users that uses Kie Server and wants a dashboard running outside from Business Central.

The dashboard can run on DashBuilder Runtime and imported in Business Central/DashBuilder to be edited.

### Dashboard Pages

The pages from this dashboards are based on default monitoring pages from Business Central and a generic Dashboard:

* **Process Reports**: Responsible to show a summary of all processes

![image](https://user-images.githubusercontent.com/359820/128437522-b093c433-556d-4741-90a7-0519965ff94c.png)

* **Task Reports**: Responsible to show a summary of all human tasks.

![image](https://user-images.githubusercontent.com/359820/128437449-bf9b85ce-1d8f-4f4c-856e-634f4fdbf394.png)

* **Process Nodes Hits**: Show heatmaps based on nodes hits from process that ran on Kie Server.

![image](https://user-images.githubusercontent.com/359820/128956001-91f5075e-c6ca-4df4-a91b-b72c4c510bb3.png)


### Setup

These dashboards make use of [Remote datasets](https://blog.kie.org/2021/08/add-data-from-kie-execution-server-for-authoring-dashboards.html) and they run on top of Kie Server advanced queries REST API.

If you want to edit these datasets in Business Central you must import the ZIP using [Content Transfer](https://access.redhat.com/documentation/en-us/red_hat_process_automation_manager/7.5/html/configuring_business_central_settings_and_properties/exporting-importing-dashbuilder-data-proc-configuring-central) and then modify each dataset to use the Kie Server connected to Business Central.

In DashBuilder WebApp or DashBuilder Runtime you must set the following system properties:

```
dashbuilder.kieserver.serverTemplate.sample-server.location={KIE SERVER LOCATION}
dashbuilder.kieserver.serverTemplate.sample-server.user={KIE SERVER USER}
dashbuilder.kieserver.serverTemplate.sample-server.password={KIE SERVER PASSWORD}
```

The following system properties should be set at least once so the remote queries are created in Kie Server:

```
dashbuilder.kieserver.serverTemplate.sample-server.replace_query=true
```

If you decide yo use Dashbuilder Runtime Quarkus distribution here's how you run it:

```
java  \
-Ddashbuilder.kieserver.serverTemplate.sample-server.replace_query=true \
-Ddashbuilder.kieserver.serverTemplate.sample-server.location={KIE SERVER LOCATION} \
-Ddashbuilder.kieserver.serverTemplate.sample-server.user={KIE SERVER USER} \
-Ddashbuilder.kieserver.serverTemplate.sample-server.password={KIE SERVER PASSWORD} \
-jar dashbuilder-runtime-app-8.0.0-alpha.jar
```

Once the datasource setup is ready, just import the [FIX LINK - Kie Server Dashboard](https://github.com/jesuino/dashbuilder-dashboards/blob/main/jBPM%20DB%20Dashboard/jbpm_reports.zip) zip file on your installation using [Content Transfer](https://access.redhat.com/documentation/en-us/red_hat_process_automation_manager/7.5/html/configuring_business_central_settings_and_properties/exporting-importing-dashbuilder-data-proc-configuring-central) or importing into [DashBuilder](https://blog.kie.org/2020/09/introducing-dashbuilder-runtime.html).

