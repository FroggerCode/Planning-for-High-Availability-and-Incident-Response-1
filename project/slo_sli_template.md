# API Service

| Category     | SLI                                                        | SLO                                                                                                         |
|--------------|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Availability | Successful HTTP requests per minute                        | 99% Successful http status codes in given time period(1hr).                                                 |
| Latency      | Overall response time of each web request                  | 90% of requests below 100ms                                                                                 |
| Error Budget | Unsuccessful requests divided by successful requests       | Error budget is defined at 10%. This means that 10% of the requests can fail and still be within the budget |
| Throughput   | Total number of web request                                | 100 request to per minute               