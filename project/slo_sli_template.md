# API Service

| Category     | SLI                                                        		| SLO                                                                                                         |
|--------------|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Availability | Successful HTTP requests divided by total request > 99% success    | 99%                                             										  |
| Latency      | Overall response time of each web request                  		| 90% of requests below 100ms                                                                                 |
| Error Budget | Unsuccessful requests divided by successful requests       		| Error budget is defined at 20%. This means that 20% of the requests can fail and still be within the budget |
| Throughput   | Total number of good requests in the last 5 minutes        		| 5 RPS indicates the application is functioning                                                              |              