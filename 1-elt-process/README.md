## Extraction Process for Athena

### Entity Relationship Diagram
[![Entity Relationship Diagram](https://mermaid.ink/img/pako:eNqNVG1vmzAQ_iuWv3STGqn7GlWV2EK1qYxMLVG_IKELPhIvYCNzJOuS_vfZQAIl6TYkBHpezse9sOepFsinHM1MwspAEStmL6HTukBFSUVAdZWgqgt20JPJYc9mHVexKYv57a3j0ABJre7uYv5-gH1LuYvwF7HUIBCKESqVJHkBt7eB1OLJFpXQ5j16hG_RyEyewV5N2itLo7c4zkoXZY7ngXaS1kmGKJaQbi5xaMwxq9f20VfqcGhKN3_88tV_ih696Ns8nETe58C3RTSYWS-qFKuRb1CxpVxV9lMgZ1KwHw89UdcW0CZdY0VtF5KuFu7VcvcPtk3hPGLhIgiO_TmlrpB22myc8G-yTOaYNEf9U1UCrVlPbMHmBqafCHop0QYJUK2s8NPNzTDMxcEbgdbsh4vvQ9vgi1341jYCWedjM__eWwQRu8rqPL8ahllqnSOotp8bpXeqGzZ2NlUOdUXriZ-VVqxAAgEEQ4MsbGugKFldCjfYCZDL5dke0pDst1Z4yiqcP3_4-KayJ3-3MP_pb4aQX3O7nAVIYZe8GaeY0xoLjLnbXgFm02itrs3OF5K04dMM8gqvOdg9eXpRKZ-SqfEo6v4Vner1DwNOYGI)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNqNVG1vmzAQ_iuWv3STGqn7GlWV2EK1qYxMLVG_IKELPhIvYCNzJOuS_vfZQAIl6TYkBHpezse9sOepFsinHM1MwspAEStmL6HTukBFSUVAdZWgqgt20JPJYc9mHVexKYv57a3j0ABJre7uYv5-gH1LuYvwF7HUIBCKESqVJHkBt7eB1OLJFpXQ5j16hG_RyEyewV5N2itLo7c4zkoXZY7ngXaS1kmGKJaQbi5xaMwxq9f20VfqcGhKN3_88tV_ih696Ns8nETe58C3RTSYWS-qFKuRb1CxpVxV9lMgZ1KwHw89UdcW0CZdY0VtF5KuFu7VcvcPtk3hPGLhIgiO_TmlrpB22myc8G-yTOaYNEf9U1UCrVlPbMHmBqafCHop0QYJUK2s8NPNzTDMxcEbgdbsh4vvQ9vgi1341jYCWedjM__eWwQRu8rqPL8ahllqnSOotp8bpXeqGzZ2NlUOdUXriZ-VVqxAAgEEQ4MsbGugKFldCjfYCZDL5dke0pDst1Z4yiqcP3_4-KayJ3-3MP_pb4aQX3O7nAVIYZe8GaeY0xoLjLnbXgFm02itrs3OF5K04dMM8gqvOdg9eXpRKZ-SqfEo6v4Vner1DwNOYGI)

### Methods
Different methods can be used depending on the use-case of delay in data is accepted by business.
Depending on it and the volume, we may opt for any of the below methods
    
#### Method 1: Trivial - Cron Schedule to Extract Data Incrementally
- Trivial Approach
[![Trivial Approach](https://mermaid.ink/img/pako:eNpNzr0OgjAQAOBXITdpQjWKE4MJERfjogwOlOGghzRCa0qJIYR3txgx3nJ_3yU3QKEFQQhlrV9FhcZ65ytXngspNukiRos5trTMGNtLsU0PRit20nk2o7_RhwQp50mw_u3nnq3YpSPTu-zUbhiiW-JFtiKF4wg-NGQalMK9MkynHNyqIQ6hKwWaBweuJtc9BVo6Cmm1gbDEuiUfsLM66VUBoTUdzSiWeDfYfNX4BqRpTRE)](https://mermaid-js.github.io/mermaid-live-editor/edit#pako:eNpNzr0OgjAQAOBXITdpQjWKE4MJERfjogwOlOGghzRCa0qJIYR3txgx3nJ_3yU3QKEFQQhlrV9FhcZ65ytXngspNukiRos5trTMGNtLsU0PRit20nk2o7_RhwQp50mw_u3nnq3YpSPTu-zUbhiiW-JFtiKF4wg-NGQalMK9MkynHNyqIQ6hKwWaBweuJtc9BVo6Cmm1gbDEuiUfsLM66VUBoTUdzSiWeDfYfNX4BqRpTRE)
- <u>Drawbacks</u>:
  This conventional approach has some drawbacks
  1. Export Issues:
     1. Performance issue to read bulk data.
     2. Difficult to split output into multiple files.
  2. Query Issues: 
     1. As input is not efficiently partitioned, Query will scan large amount of data.
     2. This inefficient storage not only costs more but also slows the query processing.

##### Data Extraction:
[![](https://mermaid.ink/img/pako:eNp9j8GKwjAQQH8lzElBWbC3Hha0LXtRZM2Ch8bDbDPasmki6QRXrP9uisruXnYOYch7PJgLVE4TpLA37lTV6FksN8qKOPmiHOXI-IkdjXdiOn0VxcdyVHyzx4obZ8WKuHZ6HEm_DnwM3PUyKZWSidjg6WV378gkCnlWDi2Rxce4w2_0ZgKV860Uw_IAf_-iJJPZPZwZQtuR_qnP_skPrH8P5M_9nGuyCBNoybfY6HjzZdAURNCSgjSuGv2XAmWv0QtHjUyFbth5SPdoOpoABnbybCtI2Qd6SnmDB4_tw7reAGdbbTQ)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNp9j8GKwjAQQH8lzElBWbC3Hha0LXtRZM2Ch8bDbDPasmki6QRXrP9uisruXnYOYch7PJgLVE4TpLA37lTV6FksN8qKOPmiHOXI-IkdjXdiOn0VxcdyVHyzx4obZ8WKuHZ6HEm_DnwM3PUyKZWSidjg6WV378gkCnlWDi2Rxce4w2_0ZgKV860Uw_IAf_-iJJPZPZwZQtuR_qnP_skPrH8P5M_9nGuyCBNoybfY6HjzZdAURNCSgjSuGv2XAmWv0QtHjUyFbth5SPdoOpoABnbybCtI2Qd6SnmDB4_tw7reAGdbbTQ)
Incremental batch load would be preferred over real-time replication due to the job stability and cost. 
However, in case of real-time data analysis, later method will be the choice.
1. <b>Incremental Batch Load</b>:- 
Either of method can be used to read data incrementally. Final choice would depend on various factor like size of database, number of tables, development-efforts and code re-usability.
   1. <ins>AWS Glue</ins>: - Use Join transformation to join the data from different tables from different database using key `orchestration_extraction_id` and accordingly get the required results.
   2. <ins>PySpark/Sqoop Job</ins>: In this case, we will use SQL override to create a custom query to get the required result for incremental processing. 

Output  from either of these step will be published  into S3 for further processing.
2. <b>Logical Real-Time Replication</b>:- 
In case of real-time data,Either of the two method can be used to  export data from Postgres db.
   1. <ins>DMS</ins>: Use AWS Data Migration Service to publish events from Postgres To S3 
   2. <ins>Stream Events Using Kinesis</ins>: Push WAL logs from postgress to push into Kinesis stream using Lambda. Lambda will convert the data from WAL into readable JSON format. Then data from kinesis can be read using AWS Glue and processed further.
   
- Connect to RDBMS using JDBC connector and Glue Crawler in AWS Glue to identify the schema and add it to data catalog automatically.
- If the schema on application side is rapidly evolving , Glue Crawler can be scheduled in regular to identify the changes and transfer it into data catalog.

- Further transformation can be applied to get the clean data
- Data target would be S3 which will be the source for Athena 
  - Target data will be partitioned to make it performant can be either dates and/or some additional fields
  - Also target data will be compressed so that data stored is compressed


