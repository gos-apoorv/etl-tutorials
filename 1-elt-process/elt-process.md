## Extraction Process for Athena

### Entity Relationship Diagram
[![Entity Relationship Diagram](https://mermaid.ink/img/pako:eNqNVG1vmzAQ_iuWv3STGqn7GlWV2EK1qYxMLVG_IKELPhIvYCNzJOuS_vfZQAIl6TYkBHpezse9sOepFsinHM1MwspAEStmL6HTukBFSUVAdZWgqgt20JPJYc9mHVexKYv57a3j0ABJre7uYv5-gH1LuYvwF7HUIBCKESqVJHkBt7eB1OLJFpXQ5j16hG_RyEyewV5N2itLo7c4zkoXZY7ngXaS1kmGKJaQbi5xaMwxq9f20VfqcGhKN3_88tV_ih696Ns8nETe58C3RTSYWS-qFKuRb1CxpVxV9lMgZ1KwHw89UdcW0CZdY0VtF5KuFu7VcvcPtk3hPGLhIgiO_TmlrpB22myc8G-yTOaYNEf9U1UCrVlPbMHmBqafCHop0QYJUK2s8NPNzTDMxcEbgdbsh4vvQ9vgi1341jYCWedjM__eWwQRu8rqPL8ahllqnSOotp8bpXeqGzZ2NlUOdUXriZ-VVqxAAgEEQ4MsbGugKFldCjfYCZDL5dke0pDst1Z4yiqcP3_4-KayJ3-3MP_pb4aQX3O7nAVIYZe8GaeY0xoLjLnbXgFm02itrs3OF5K04dMM8gqvOdg9eXpRKZ-SqfEo6v4Vner1DwNOYGI)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNqNVG1vmzAQ_iuWv3STGqn7GlWV2EK1qYxMLVG_IKELPhIvYCNzJOuS_vfZQAIl6TYkBHpezse9sOepFsinHM1MwspAEStmL6HTukBFSUVAdZWgqgt20JPJYc9mHVexKYv57a3j0ABJre7uYv5-gH1LuYvwF7HUIBCKESqVJHkBt7eB1OLJFpXQ5j16hG_RyEyewV5N2itLo7c4zkoXZY7ngXaS1kmGKJaQbi5xaMwxq9f20VfqcGhKN3_88tV_ih696Ns8nETe58C3RTSYWS-qFKuRb1CxpVxV9lMgZ1KwHw89UdcW0CZdY0VtF5KuFu7VcvcPtk3hPGLhIgiO_TmlrpB22myc8G-yTOaYNEf9U1UCrVlPbMHmBqafCHop0QYJUK2s8NPNzTDMxcEbgdbsh4vvQ9vgi1341jYCWedjM__eWwQRu8rqPL8ahllqnSOotp8bpXeqGzZ2NlUOdUXriZ-VVqxAAgEEQ4MsbGugKFldCjfYCZDL5dke0pDst1Z4yiqcP3_4-KayJ3-3MP_pb4aQX3O7nAVIYZe8GaeY0xoLjLnbXgFm02itrs3OF5K04dMM8gqvOdg9eXpRKZ-SqfEo6v4Vner1DwNOYGI)

### Assumptions
- Incremental updates are done to table

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
#### Method 2: AWS Glue To Extract Data 
- Use AWS Glue to connect to PostgreSQL
- Scheduling Glue Job will help to export data into S3 in partitioned format
- It will also help to add data into data catalog
#### Method 3: DB Triggers to Extract Data
#### Method 4: AWS Lambda






