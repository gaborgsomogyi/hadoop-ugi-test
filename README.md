# hadoop-ugi-test

Standalone test app how UGI works.

## How to build
In order to build the project one needs maven and java.
Please make sure to:
* set Flink version in `pom.xml` file with `hadoop.version` parameter

```
mvn clean install
```

## How to use
```
$ kinit user
Password for user@EXAMPLE.COM:
$ klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: user@EXAMPLE.COM

Valid starting     Expires            Service principal
10/25/22 12:29:56  10/26/22 12:29:52  krbtgt/EXAMPLE.COM@EXAMPLE.COM
$ java -jar target/hadoop-ugi-test-1.0.jar
WARNING: sun.reflect.Reflection.getCallerClass is not supported. This will impact performance.
12:30:01,932 INFO  HadoopUgiTest [] - Starting Hadoop UGI test app
12:30:01,959 DEBUG MutableMetricsFactory [] - field org.apache.hadoop.metrics2.lib.MutableRate org.apache.hadoop.security.UserGroupInformation$UgiMetrics.getGroups with annotation @org.apache.hadoop.metrics2.annotation.Metric(always=false, sampleName="Ops", valueName="Time", about="", interval=10, type=DEFAULT, value={"GetGroups"})
12:30:01,964 DEBUG MutableMetricsFactory [] - field org.apache.hadoop.metrics2.lib.MutableRate org.apache.hadoop.security.UserGroupInformation$UgiMetrics.loginFailure with annotation @org.apache.hadoop.metrics2.annotation.Metric(always=false, sampleName="Ops", valueName="Time", about="", interval=10, type=DEFAULT, value={"Rate of failed kerberos logins and latency (milliseconds)"})
12:30:01,965 DEBUG MutableMetricsFactory [] - field org.apache.hadoop.metrics2.lib.MutableRate org.apache.hadoop.security.UserGroupInformation$UgiMetrics.loginSuccess with annotation @org.apache.hadoop.metrics2.annotation.Metric(always=false, sampleName="Ops", valueName="Time", about="", interval=10, type=DEFAULT, value={"Rate of successful kerberos logins and latency (milliseconds)"})
12:30:01,965 DEBUG MutableMetricsFactory [] - field private org.apache.hadoop.metrics2.lib.MutableGaugeInt org.apache.hadoop.security.UserGroupInformation$UgiMetrics.renewalFailures with annotation @org.apache.hadoop.metrics2.annotation.Metric(always=false, sampleName="Ops", valueName="Time", about="", interval=10, type=DEFAULT, value={"Renewal failures since last successful login"})
12:30:01,966 DEBUG MutableMetricsFactory [] - field private org.apache.hadoop.metrics2.lib.MutableGaugeLong org.apache.hadoop.security.UserGroupInformation$UgiMetrics.renewalFailuresTotal with annotation @org.apache.hadoop.metrics2.annotation.Metric(always=false, sampleName="Ops", valueName="Time", about="", interval=10, type=DEFAULT, value={"Renewal failures since startup"})
12:30:01,970 DEBUG MetricsSystemImpl [] - UgiMetrics, User and group related metrics
12:30:02,032 DEBUG Shell [] - Failed to detect a valid hadoop home directory
java.io.FileNotFoundException: HADOOP_HOME and hadoop.home.dir are unset.
	at org.apache.hadoop.util.Shell.checkHadoopHomeInner(Shell.java:467) ~[hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.util.Shell.checkHadoopHome(Shell.java:438) ~[hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.util.Shell.<clinit>(Shell.java:515) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.util.StringUtils.<clinit>(StringUtils.java:79) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.conf.Configuration.getBoolean(Configuration.java:1712) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.security.SecurityUtil.setConfigurationInternal(SecurityUtil.java:99) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.security.SecurityUtil.<clinit>(SecurityUtil.java:88) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.security.UserGroupInformation.initialize(UserGroupInformation.java:312) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.security.UserGroupInformation.ensureInitialized(UserGroupInformation.java:300) [hadoop-ugi-test-1.0.jar:?]
	at org.apache.hadoop.security.UserGroupInformation.getCurrentUser(UserGroupInformation.java:575) [hadoop-ugi-test-1.0.jar:?]
	at com.apple.hadoop.HadoopUgiTest.main(HadoopUgiTest.java:33) [hadoop-ugi-test-1.0.jar:?]
12:30:02,052 DEBUG Shell [] - setsid exited with exit code 0
12:30:02,052 DEBUG SecurityUtil [] - Setting hadoop.security.token.service.use_ip to true
12:30:02,085 DEBUG Groups [] -  Creating new Groups object
12:30:02,088 DEBUG NativeCodeLoader [] - Trying to load the custom-built native-hadoop library...
12:30:02,088 DEBUG NativeCodeLoader [] - Failed to load native-hadoop with error: java.lang.UnsatisfiedLinkError: no hadoop in java.library.path: [/usr/java/packages/lib, /usr/lib/x86_64-linux-gnu/jni, /lib/x86_64-linux-gnu, /usr/lib/x86_64-linux-gnu, /usr/lib/jni, /lib, /usr/lib]
12:30:02,089 DEBUG NativeCodeLoader [] - java.library.path=/usr/java/packages/lib:/usr/lib/x86_64-linux-gnu/jni:/lib/x86_64-linux-gnu:/usr/lib/x86_64-linux-gnu:/usr/lib/jni:/lib:/usr/lib
12:30:02,089 WARN  NativeCodeLoader [] - Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
12:30:02,090 DEBUG JniBasedUnixGroupsMappingWithFallback [] - Falling back to shell based
12:30:02,091 DEBUG JniBasedUnixGroupsMappingWithFallback [] - Group mapping impl=org.apache.hadoop.security.ShellBasedUnixGroupsMapping
12:30:02,102 DEBUG Groups [] - Group mapping impl=org.apache.hadoop.security.JniBasedUnixGroupsMappingWithFallback; cacheTimeout=300000; warningDeltaMs=5000
12:30:02,142 DEBUG UserGroupInformation$HadoopLoginModule [] - Hadoop login
12:30:02,144 DEBUG UserGroupInformation$HadoopLoginModule [] - hadoop login commit
12:30:02,146 DEBUG UserGroupInformation$HadoopLoginModule [] - Using kerberos user: user@EXAMPLE.COM
12:30:02,146 DEBUG UserGroupInformation$HadoopLoginModule [] - Using user: "user@EXAMPLE.COM" with name: user@EXAMPLE.COM
12:30:02,147 DEBUG UserGroupInformation$HadoopLoginModule [] - User entry: "user@EXAMPLE.COM"
12:30:02,147 DEBUG UserGroupInformation [] - UGI loginUser: user@EXAMPLE.COM (auth:KERBEROS)
12:30:02,149 INFO  HadoopUgiTest [] - UGI current user has credentials: true
12:30:02,150 DEBUG UserGroupInformation$AutoRenewalForUserCredsRunnable [] - Current time is 1666701002150, next refresh is 1666770112800
```
