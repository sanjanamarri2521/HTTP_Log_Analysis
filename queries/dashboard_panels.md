# DNS Dashboard Panels SPL Queries

## Top 10 IP requests
```spl
source="access.log.zip:*" host="SanjuPranava" | top clientip limit=10
```
## Most Accessed Files
```spl
source="access.log.zip:*" host="SanjuPranava" | top file limit=10
```
## Requests per Hour
```spl
source="access.log.zip:*" host="SanjuPranava" | timechart span=1h count
```
## HTTP Status Code Distribution
```spl
source="access.log.zip:*" host="SanjuPranava" | stats count by status

```
## File Size Distribution
```spl
source="access.log.zip:*" host="SanjuPranava" | bucket bytes span=500 | stats count by bytes
```
## Requests by HTTP Version
```spl
source="access.log.zip:*" host="SanjuPranava" | stats count by version
```
## Request Timing Statistics
```spl
source="access.log.zip:*" host="SanjuPranava"| stats max(req_time) as max_time, min(req_time) as min_time by clientip| sort - max_time | head 10
```
