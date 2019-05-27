### Common description:  
```
The check monitors AWS metrics via CloudWatch.
The check requires AWS access keys
```

### Options:  
```
 -h, --help            show this help message and exit
  -a ACCESS_KEY, --access-key ACCESS_KEY
                        AWS API Access Key
  -s SECRET_KEY, --secret-key SECRET_KEY
                        AWS API Secret Key
  -r REGION, --region REGION
                        AWS region
  -n NAMESPACE, --namespace NAMESPACE
                        Namespace name for CloudWatch. Example for RDS -
                        AWS/RDS, All possible values in official documentation
                        - https://docs.aws.amazon.com/AmazonCloudWatch/latest/
                        monitoring/aws-namespaces.html
  -m METRIC, --metric METRIC
                        CloudWatch metric. Example for CPU - CPUUtilization
  -dn DNAME [DNAME ...], --dimensions-name DNAME [DNAME ...]
                        List of dimension parameter name. See Readme.md for
                        additional information -
                        https://bitbucket.org/thumbtacktech/lineate-support-
                        team-monitoring-
                        checks/src/master/check_cloudwatch_metric/
  -dv DVALUE [DVALUE ...], --dimensions-value DVALUE [DVALUE ...]
                        List of dimension parameter value. See Readme.md for
                        additional information -
                        https://bitbucket.org/thumbtacktech/lineate-support-
                        team-monitoring-
                        checks/src/master/check_cloudwatch_metric/
  -w WARN_THRESHOLD, --warn WARN_THRESHOLD
                        Warning limit of metric
  -c CRIT_THRESHOLD, --crit CRIT_THRESHOLD
                        Critical limit of metric
  -b BELLOW, --bellow BELLOW
                        Set to "true" if you need check metric mellow w/c
                        thresholds
  -i IGNORE_MISSING, --ignore-missing IGNORE_MISSING
                        Set to "true" if you need to ignore missing values
  -stat STAT, --statistics STAT
                        The statistic to return. One from list - SampleCount,
                        Average, Sum, Minimum, Maximum. By default: Average
  -p PERIOD, --period PERIOD
                        The granularity, in seconds, of the returned data
                        points. Period must be a value in the set [ 1, 5, 10,
                        30 ] or multiple of 60. By default: 300
  -ext EXT, --extended EXT
                        Set to true for get extended metric, by default false                                                
```

### Command line example:  
```
For RDS database
-n "AWS/RDS" -dn "DBInstanceIdentifier" -dv "cavendishsq-sc-db"

for EC2 instance
-n "AWS/EC2" -dn "InstanceId" -dv "i-b2827759"

for CloudFront 
-n "AWS/CloudFront" -dn DistributionId Region -dv E2PA05DFSEH7OS Global

```

### Nagios/Icinga service example:  
``` 

```

### Nagios/Icinga command example:  
``` 
define command {
        command_name    check_cloudwatch_metric
        command_line    /usr/lib/nagios/plugins/check_cloudwatch_metric.py -a $ARG1$ -s $ARG2$ -r $ARG3$ -n $ARG4$ -m $ARG5$ -dn $ARG6$ -dv $ARG7$ -b $ARG8$ -w $ARG9$ -c $ARG10$ "$ARG11"
        }


```

# test
