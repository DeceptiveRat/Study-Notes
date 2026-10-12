1. Kibana Query Language (KQL)
- text-based query language for filtering data
- no role aggregating, transforming, or sorting data

2. KQL usage
- search with field:value pairs
   - event.code:4625
- fields can be omitted
   - svc-sql1=> returns events with string "svc-sql1" included
- values can be omitted
   - http.request.method: * => returns events where field http.request.method exists
   - http.request: null pointer => returns events where field http.request contains "null" and "pointer" in any order
   - http.request: "null pointer" => returns events where field http.request contains "null pointer"
- certain values must be escaped by a backslash: \():<>"*
   - http.request.referrer: https\://example.com
   - http.request.referrer: "https://example.com"
- comparison operation is allowed
   - http.response.bytes < 1000 or http.response.bytes >= 100
   - @timestamp < now-2w
- wildcards are supported
   - http.response.status_code: 4*
- querying nested fields requires a special syntax
   - user:{ first: "Alice" and last: "White" }

reference:
- HTB academy
- Elastic - KQL: <https://www.elastic.co/docs/explore-analyze/query-filter/languages/kql>