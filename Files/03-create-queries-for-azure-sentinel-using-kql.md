# Create queries with visualation using Kusto Query Language (KQL)

**Note** Successful completion of this demo depends on completing all of the steps in the  [Pre-requisites document](00-prerequisites.md). 

## Access the KQL testing area.

In this task, you will access a Log Analytics environment where you can practice writing KQL statements.

2. Go to https://aka.ms/lademo in your browser.

### Create visualizations in KQL with the Render Operator

In this task, you will use generate visualizations with KQL statements.

1. The following statement demonstrates the render function visualizing results with a barchart. In the Query Window. Enter the following statement and select **run**: 

```KQL
SecurityEvent 
| summarize count() by Account
| render barchart
```

2. The following statement demonstrates the render function visualizing results with a time series.

The bin() function rounds values down to an integer multiple of the given bin size.  Used frequently in combination with summarize by .... If you have a scattered set of values, the values are grouped into a smaller set of specific values.  Combining the generated time series and pipe to a render operator with a type of timechart provides a time series visualization. In the Query Window. Enter the following statement and select **run**: 

```KQL
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart
```

## You have completed the demo.

