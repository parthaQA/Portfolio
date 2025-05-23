Objective:

Performance Testing
Used JMeter to simulate load on the API (e.g., 100 users in 1
minute).

Scenario:
Simulate 100 virtual users in 1 minute doing the following:
• Logging in  (https://dummyjson.com/auth/login)
• Fetching products (https://dummyjson.com/products?limit={{limit}})
• Adding items to a cart (https://dummyjson.com/carts/add)

Goals:
• Monitor response times, error rates, throughput
• Identify any bottlenecks or failures under load

Report:
Added jmeter inbuilt report View Result tree, Summary report, Aggregate report. 




Note: I am using a windows machine therefore all instructions are for as per windows machine.

1. Download and Install JMeter
Install Java (JDK or JRE):
Set path

JMeter requires Java 8 or higher.

Check if Java is installed:
Open command promt type below command
java -version
If not, download Java and install it.

Set JAVA_HOME environment variable.

Download JMeter:

Go to the official JMeter website.

Download the binary release (e.g., .zip file).

Extract JMeter:

Unzip the downloaded file (e.g., apache-jmeter-5.6.3.zip) to a directory like C:\jmeter\apache-jmeter-5.6.3.

2. Verify JMeter Installation
Open Command Prompt.

Navigate to the JMeter bin folder:

cd C:\jmeter\apache-jmeter-5.6.3\bin
Launch JMeter GUI (to check):
Open command promt type below command:

jmeter.bat
It should open the JMeter interface.
Open the .jmx file in jmeter.

Run .jmx file in commandline: 
jmeter -n -t Dummyjson_performance.jmx -Jthreads=100 -Jrampup=60 -l result/result.jtl

-Jthreads=100 this is for 100 virtual user for each test.
-Jrampup=60 this is Ramp-up time is 60 seconds.

Generate HTML Report:
jmeter.bat -g result/result.jtl -o result/report


To run .jmx file in Gitlab pipeline push the code to gitlab repo. It will trigger the pipeline automatically.