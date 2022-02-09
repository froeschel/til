# log analytics workspace

Log Analytics Workspace is an environment for log data. Solutions in Azure can be configured to store their data in a specific log analytis workspace. In our case we have reconfigured our old Application Insights instance to write all data to a new log analytics workspace. This was required, because Azure will deprecate the old Application Insight instances. 