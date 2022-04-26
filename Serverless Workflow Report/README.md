A Summary report for Serverless Workflow services. It requires data index to run. The query should return a JSON with the following format:


~~~
{
   "data":{
      "ProcessInstances":[
         {
            "id":"0aa4eba3-f0c8-4918-a559-7a7f065047df",
            "processId":"jsongreet",
            "processName":"Greeting workflow",
            "serviceUrl":"http://swf-greeting-persistence-monitoring-dashbuilder.kie-tooling-0ad6762cc85bcef5745bb684498c2436-0000.us-south.containers.appdomain.cloud",
            "state":"COMPLETED",
            "start":"2022-03-09T05:02:51.334Z",
            "end":"2022-03-09T05:02:51.399Z",
            "lastUpdate":"2022-03-09T05:02:51.426Z",
            "error":null
         },
         {
            "id":"48bbb8fa-e04a-48ec-925d-d3af9699d266",
            "processId":"yamlgreet",
            "processName":"Greeting workflow",
            "serviceUrl":"http://swf-greeting-persistence-monitoring-dashbuilder.kie-tooling-0ad6762cc85bcef5745bb684498c2436-0000.us-south.containers.appdomain.cloud",
            "state":"COMPLETED",
            "start":"2022-03-09T14:08:05.779Z",
            "end":"2022-03-09T14:08:05.897Z",
            "lastUpdate":"2022-03-09T14:08:05.922Z",
            "error":null
         }
      ]
   }
}
~~~
