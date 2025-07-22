Logging is useful to convey a multitude of information about system state and function. But sometimes useful information gets lost in stacked piles of log. We should follow 12 main guidelines when we decide to log 
### Establish clear objectives
Putting down clear objective and intention of a particular log makes  
### Use log levels correctly:

- `INFO`: Significant and noteworthy events.
- `WARN`: Abnormal situations that may indicate future problems.
- `ERROR`: Unrecoverable errors that affect a specific operation.
- `FATAL`: Unrecoverable errors that affect the entire program

### Structure logs:
Having the logs in a structured format like json or xml not only make it readable but also parse-able.  Could be useful if you implement observability in your system.

### Entries should be meaningful:
It should convey as much context as possible . Especially at Error or Fatal log levels.

For example Essential details can include:

- Request or correlation IDs
- User IDs
- Database table names and metadata
- Stack traces for errors
### Sample your logs
Especially for high-frequency data. You wouldn't want to clog the output stream with logs.
example:
```
import logging
from random import SystemRandom


class ProbabilityFilter(logging.Filter):
    probability = 0.10
    cryptogen = SystemRandom()

    def filter(self, record):
        return self.cryptogen.random() < self.probability



logger = logging.getLogger('test_logger')
logger.setLevel('INFO')
logger.addFilter(ProbabilityFilter())
logger.addHandler(logging.StreamHandler())


for i in range(100):
    logger.info("Logging number: {}".format(i))
```

### Employ a canonical line per iteration
[A canonical log line](https://stripe.com/blog/canonical-log-lines) is a single, comprehensive log entry that is created at the end of each request to your service. This record is designed to be a condensed summary that includes all the essential information about the request, making it easier to understand what happened without needing to piece together information from multiple log entries

### Aggregate and Centralize your logs
By funneling all logs into a centralized log management system, you'll create a singular, searchable source of truth that simplifies monitoring, analysis, and debugging efforts across your entire infrastructure.

### Configure a retention policy
Logs occupy space. We should be able to define a policy discard logs either by age or space occupied.
Remember also to set up an appropriate [log rotation](https://betterstack.com/community/guides/logging/how-to-manage-log-files-with-logrotate-on-ubuntu-20-04/) strategy to keep log file sizes in check on your application hosts.

### Protect logs in case of sensitive information
Certain logs, such as database logs, tend to contain some degree of sensitive information. Therefore, you must take steps to protect and secure the collected data to ensure that it can only be accessed by personnel who genuinely need to use it (such as for debugging problems).

Some measures include encrypting the logs at rest and in transit using strong algorithms and keys so that the data is unreadable by unauthorized parties, even if it is intercepted or compromised.

Choose a compliant log management provider that provides access control and audit logging so that only authorized personnel can access sensitive log data, and all interactions with the logs are tracked for security and compliance purposes.

Additionally, you should verify the provider's practices regarding the handling, storage, access, and disposal of your log data when it is no longer needed.

### Don't ignore cost of logging
There is obviously a performance cost to logging. Profile it if you can.

### Don't rely on logs for monitoring
Logs don't touch every part of the code, a very well designed metric can tell more than logging .








