# OpenSearch Refresh Interval
OpenSearch has a default refresh interval of 1 second. The duration of the refresh interval determines how long it takes a document sent to OpenSearch to be search-able. 

Refreshing an index can be a resource intensive operation, decreasing the frequency of refreshes can reduce the load on an OpenSearch domain at the cost of decreasing how quickly documents become search-able. 

In summary - if you do not need updates / new documents to be search-able within 1 second. Increasing the refresh interval can result in lower load on an OpenSearch domain. This can be especially helpful for write intensive work loads.

The information below describes how to use the OpenSearch APIs to adjust the refresh interval for an index

## Change the OpenSeach Refresh Interval for an Index

Running 

```
PUT /sample-data/_settings
{
    "index" : {
        "refresh_interval" : "30s"
    }
}
```

Will adjust the refresh interval of the index **sample-data** from the default of 1 second to 30 seconds. Setting the refresh interal to -1 would disable refreshing. If the refresh interval is -1 refreshes will only happen when they are manually refreshed

## Refresh an Index

Running

```
POST sample-data/_refresh
```
 
 Will manually force a refresh on the index **sample-data**
