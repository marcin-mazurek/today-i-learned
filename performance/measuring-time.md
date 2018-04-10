## How to measure time in performance metrics?

To measure the performance, eg. a server response time - do not compute the average. Average is rarely going to tell you the truth, unless values are almost equal.
If you want a real metric, use percentiles instead.

Percentiles tell you "x percent of your values are less than y",
eg. 95th percentile tells you that "95% of your requests take less than 200ms". 100th percentile is the worst case.

Amazon uses percentiles extensively for optimizing AWS - they usually look at the 99.9th percentile.
