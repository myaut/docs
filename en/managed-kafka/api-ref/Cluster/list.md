---
editable: false
---

# Method list
Retrieves the list of Apache Kafka® clusters that belong to the specified folder.
 

 
## HTTP request {#https-request}
```
GET https://mdb.api.cloud.yandex.net/managed-kafka/v1/clusters
```
 
## Query parameters {#query_params}
 
Parameter | Description
--- | ---
folderId | Required. ID of the folder to list Apache Kafka® clusters in.  To get the folder ID, make a [list](/docs/resource-manager/api-ref/Folder/list) request.  The maximum string length in characters is 50.
pageSize | The maximum number of results per page to return.  If the number of available results is larger than [pageSize](/docs/managed-kafka/api-ref/Cluster/list#query_params), the service returns a [nextPageToken](/docs/managed-kafka/api-ref/Cluster/list#responses) that can be used to get the next page of results in subsequent list requests.  The maximum value is 1000.
pageToken | Page token.  To get the next page of results, set [pageToken](/docs/managed-kafka/api-ref/Cluster/list#query_params) to the [nextPageToken](/docs/managed-kafka/api-ref/Cluster/list#responses) returned by a previous list request.  The maximum string length in characters is 100.
filter | Filter support is not currently implemented. Any filters are ignored.  The maximum string length in characters is 1000.
 
## Response {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "clusters": [
    {
      "id": "string",
      "folderId": "string",
      "createdAt": "string",
      "name": "string",
      "description": "string",
      "labels": "object",
      "environment": "string",
      "monitoring": [
        {
          "name": "string",
          "description": "string",
          "link": "string"
        }
      ],
      "config": {
        "version": "string",
        "kafka": {
          "resources": {
            "resourcePresetId": "string",
            "diskSize": "string",
            "diskTypeId": "string"
          },

          // `clusters[].config.kafka` includes only one of the fields `kafkaConfig_2_1`, `kafkaConfig_2_6`
          "kafkaConfig_2_1": {
            "compressionType": "string",
            "logFlushIntervalMessages": "integer",
            "logFlushIntervalMs": "integer",
            "logFlushSchedulerIntervalMs": "integer",
            "logRetentionBytes": "integer",
            "logRetentionHours": "integer",
            "logRetentionMinutes": "integer",
            "logRetentionMs": "integer"
          },
          "kafkaConfig_2_6": {
            "compressionType": "string",
            "logFlushIntervalMessages": "integer",
            "logFlushIntervalMs": "integer",
            "logFlushSchedulerIntervalMs": "integer",
            "logRetentionBytes": "integer",
            "logRetentionHours": "integer",
            "logRetentionMinutes": "integer",
            "logRetentionMs": "integer"
          },
          // end of the list of possible fields`clusters[].config.kafka`

        },
        "zookeeper": {
          "resources": {
            "resourcePresetId": "string",
            "diskSize": "string",
            "diskTypeId": "string"
          }
        },
        "zoneId": [
          "string"
        ],
        "brokersCount": "integer",
        "assignPublicIp": true
      },
      "networkId": "string",
      "health": "string",
      "status": "string"
    }
  ],
  "nextPageToken": "string"
}
```

 
Field | Description
--- | ---
clusters[] | **object**<br><p>An Apache Kafka® cluster resource. For more information, see the <a href="/docs/managed-kafka/concepts">Concepts</a> section of the documentation.</p> 
clusters[].<br>id | **string**<br><p>ID of the Apache Kafka® cluster. This ID is assigned at creation time.</p> 
clusters[].<br>folderId | **string**<br><p>ID of the folder that the Apache Kafka® cluster belongs to.</p> 
clusters[].<br>createdAt | **string** (date-time)<br><p>Creation timestamp.</p> <p>String in <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a> text format.</p> 
clusters[].<br>name | **string**<br><p>Name of the Apache Kafka® cluster. The name must be unique within the folder. 1-63 characters long. Value must match the regular expression <code>[a-zA-Z0-9_-]*</code>.</p> 
clusters[].<br>description | **string**<br><p>Description of the Apache Kafka® cluster. 0-256 characters long.</p> 
clusters[].<br>labels | **object**<br><p>Custom labels for the Apache Kafka® cluster as <code>key:value</code> pairs. A maximum of 64 labels per resource is allowed.</p> 
clusters[].<br>environment | **string**<br><p>Deployment environment of the Apache Kafka® cluster.</p> <ul> <li>PRODUCTION: stable environment with a conservative update policy when only hotfixes are applied during regular maintenance.</li> <li>PRESTABLE: environment with a more aggressive update policy when new versions are rolled out irrespective of backward compatibility.</li> </ul> 
clusters[].<br>monitoring[] | **object**<br><p>Metadata of monitoring system.</p> 
clusters[].<br>monitoring[].<br>name | **string**<br><p>Name of the monitoring system.</p> 
clusters[].<br>monitoring[].<br>description | **string**<br><p>Description of the monitoring system.</p> 
clusters[].<br>monitoring[].<br>link | **string**<br><p>Link to the monitoring system charts for the Apache Kafka® cluster.</p> 
clusters[].<br>config | **object**<br><p>Configuration of the Apache Kafka® cluster.</p> 
clusters[].<br>config.<br>version | **string**<br><p>Version of Apache Kafka® used in the cluster. Possible values: <code>2.1</code>, <code>2.6</code>.</p> 
clusters[].<br>config.<br>kafka | **object**<br><p>Configuration and resource allocation for Kafka brokers.</p> 
clusters[].<br>config.<br>kafka.<br>resources | **object**<br>Resources allocated to Kafka brokers.<br>
clusters[].<br>config.<br>kafka.<br>resources.<br>resourcePresetId | **string**<br><p>ID of the preset for computational resources available to a host (CPU, memory, etc.). All available presets are listed in the <a href="/docs/managed-kafka/concepts/instance-types">documentation</a>.</p> 
clusters[].<br>config.<br>kafka.<br>resources.<br>diskSize | **string** (int64)<br><p>Volume of the storage available to a host, in bytes.</p> 
clusters[].<br>config.<br>kafka.<br>resources.<br>diskTypeId | **string**<br><p>Type of the storage environment for the host.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1 | **object** <br>`clusters[].config.kafka` includes only one of the fields `kafkaConfig_2_1`, `kafkaConfig_2_6`<br><br><p>Kafka version 2.1 broker configuration.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>compressionType | **string**<br><p>Сluster topics compression type.</p> <ul> <li>COMPRESSION_TYPE_UNCOMPRESSED: no codec (uncompressed).</li> <li>COMPRESSION_TYPE_ZSTD: Zstandard codec.</li> <li>COMPRESSION_TYPE_LZ4: LZ4 codec.</li> <li>COMPRESSION_TYPE_SNAPPY: Snappy codec.</li> <li>COMPRESSION_TYPE_GZIP: GZip codec.</li> <li>COMPRESSION_TYPE_PRODUCER: the codec to use is set by a producer (can be any of <code>ZSTD</code>, <code>LZ4</code>, <code>GZIP</code> or <code>SNAPPY</code> codecs).</li> </ul> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logFlushIntervalMessages | **integer** (int64)<br><p>The number of messages accumulated on a log partition before messages are flushed to disk.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>flushMessages</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logFlushIntervalMs | **integer** (int64)<br><p>The maximum time (in milliseconds) that a message in any topic is kept in memory before flushed to disk. If not set, the value of <code>logFlushSchedulerIntervalMs</code> is used.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>flushMs</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logFlushSchedulerIntervalMs | **integer** (int64)<br><p>The frequency of checks (in milliseconds) for any logs that need to be flushed to disk. This check is done by the log flusher.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logRetentionBytes | **integer** (int64)<br><p>Partition size limit; Kafka will discard old log segments to free up space if <code>delete</code> <code>cleanupPolicy</code> is in effect. This setting is helpful if you need to control the size of a log due to limited disk space.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>retentionBytes</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logRetentionHours | **integer** (int64)<br><p>The number of hours to keep a log segment file before deleting it.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logRetentionMinutes | **integer** (int64)<br><p>The number of minutes to keep a log segment file before deleting it.</p> <p>If not set, the value of <code>logRetentionHours</code> is used.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_1.<br>logRetentionMs | **integer** (int64)<br><p>The number of milliseconds to keep a log segment file before deleting it.</p> <p>If not set, the value of <code>logRetentionMinutes</code> is used.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>retentionMs</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6 | **object** <br>`clusters[].config.kafka` includes only one of the fields `kafkaConfig_2_1`, `kafkaConfig_2_6`<br><br><p>Kafka version 2.6 broker configuration.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>compressionType | **string**<br><p>Сluster topics compression type.</p> <ul> <li>COMPRESSION_TYPE_UNCOMPRESSED: no codec (uncompressed).</li> <li>COMPRESSION_TYPE_ZSTD: Zstandard codec.</li> <li>COMPRESSION_TYPE_LZ4: LZ4 codec.</li> <li>COMPRESSION_TYPE_SNAPPY: Snappy codec.</li> <li>COMPRESSION_TYPE_GZIP: GZip codec.</li> <li>COMPRESSION_TYPE_PRODUCER: the codec to use is set by a producer (can be any of <code>ZSTD</code>, <code>LZ4</code>, <code>GZIP</code> or <code>SNAPPY</code> codecs).</li> </ul> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logFlushIntervalMessages | **integer** (int64)<br><p>The number of messages accumulated on a log partition before messages are flushed to disk.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>flushMessages</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logFlushIntervalMs | **integer** (int64)<br><p>The maximum time (in milliseconds) that a message in any topic is kept in memory before flushed to disk. If not set, the value of <code>logFlushSchedulerIntervalMs</code> is used.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>flushMs</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logFlushSchedulerIntervalMs | **integer** (int64)<br><p>The frequency of checks (in milliseconds) for any logs that need to be flushed to disk. This check is done by the log flusher.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logRetentionBytes | **integer** (int64)<br><p>Partition size limit; Kafka will discard old log segments to free up space if <code>delete</code> <code>cleanupPolicy</code> is in effect. This setting is helpful if you need to control the size of a log due to limited disk space.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>retentionBytes</code> setting.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logRetentionHours | **integer** (int64)<br><p>The number of hours to keep a log segment file before deleting it.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logRetentionMinutes | **integer** (int64)<br><p>The number of minutes to keep a log segment file before deleting it.</p> <p>If not set, the value of <code>logRetentionHours</code> is used.</p> 
clusters[].<br>config.<br>kafka.<br>kafkaConfig_2_6.<br>logRetentionMs | **integer** (int64)<br><p>The number of milliseconds to keep a log segment file before deleting it.</p> <p>If not set, the value of <code>logRetentionMinutes</code> is used.</p> <p>This is the global cluster-level setting that can be overridden on a topic level by using the <code>retentionMs</code> setting.</p> 
clusters[].<br>config.<br>zookeeper | **object**<br><p>Configuration and resource allocation for ZooKeeper hosts.</p> 
clusters[].<br>config.<br>zookeeper.<br>resources | **object**<br><p>Resources allocated to ZooKeeper hosts.</p> 
clusters[].<br>config.<br>zookeeper.<br>resources.<br>resourcePresetId | **string**<br><p>ID of the preset for computational resources available to a host (CPU, memory, etc.). All available presets are listed in the <a href="/docs/managed-kafka/concepts/instance-types">documentation</a>.</p> 
clusters[].<br>config.<br>zookeeper.<br>resources.<br>diskSize | **string** (int64)<br><p>Volume of the storage available to a host, in bytes.</p> 
clusters[].<br>config.<br>zookeeper.<br>resources.<br>diskTypeId | **string**<br><p>Type of the storage environment for the host.</p> 
clusters[].<br>config.<br>zoneId[] | **string**<br><p>IDs of availability zones where Kafka brokers reside.</p> 
clusters[].<br>config.<br>brokersCount | **integer** (int64)<br><p>The number of Kafka brokers deployed in each availability zone.</p> 
clusters[].<br>config.<br>assignPublicIp | **boolean** (boolean)<br><p>The flag that defines whether a public IP address is assigned to the cluster. If the value is <code>true</code>, then Apache Kafka® cluster is available on the Internet via it's public IP address.</p> 
clusters[].<br>networkId | **string**<br><p>ID of the network that the cluster belongs to.</p> 
clusters[].<br>health | **string**<br><p>Aggregated cluster health.</p> <ul> <li>HEALTH_UNKNOWN: state of the cluster is unknown (<code>health</code> of all hosts in the cluster is <code>UNKNOWN</code>).</li> <li>ALIVE: cluster is alive and well (<code>health</code> of all hosts in the cluster is <code>ALIVE</code>).</li> <li>DEAD: cluster is inoperable (<code>health</code> of all hosts in the cluster is <code>DEAD</code>).</li> <li>DEGRADED: cluster is in degraded state (<code>health</code> of at least one of the hosts in the cluster is not <code>ALIVE</code>).</li> </ul> 
clusters[].<br>status | **string**<br><p>Current state of the cluster.</p> <ul> <li>STATUS_UNKNOWN: cluster state is unknown.</li> <li>CREATING: cluster is being created.</li> <li>RUNNING: cluster is running normally.</li> <li>ERROR: cluster encountered a problem and cannot operate.</li> <li>UPDATING: cluster is being updated.</li> <li>STOPPING: cluster is stopping.</li> <li>STOPPED: cluster stopped.</li> <li>STARTING: cluster is starting.</li> </ul> 
nextPageToken | **string**<br><p>Token that allows you to get the next page of results for list requests.</p> <p>If the number of results is larger than <a href="/docs/managed-kafka/api-ref/Cluster/list#query_params">pageSize</a>, use <a href="/docs/managed-kafka/api-ref/Cluster/list#responses">nextPageToken</a> as the value for the <a href="/docs/managed-kafka/api-ref/Cluster/list#query_params">pageToken</a> parameter in the next list request. Each subsequent list request will have its own <a href="/docs/managed-kafka/api-ref/Cluster/list#responses">nextPageToken</a> to continue paging through the results.</p> 