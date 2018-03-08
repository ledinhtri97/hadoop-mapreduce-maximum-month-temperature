# hadoop-mapreduce-maximum-month-temperature

# download hadoop-core-1.2.1.jar, which is used to compile and execute the
# MapReduce program.
# Make sure you had started the hadoop by `start-all.sh`, to check
# it work well, type command `sudo jps`
# and when done your job
# let `stop-all.sh`.
# Step to compile program.

-step 1: the following command is to create a directory to store the compiled
java classes

```$ mkdir lab```

-step 2: compiling the MaxMomTem.java and creating a jar for the program

```$ javac -classpath hadoop-core-1.2.1.jar -d lab MaxMomTem.java```
```$ jar -cvf lab.jar -C lab/ .```

-step 3: The following command is used to create an input directory in HDFS.

```$ hadoop fs -mkdir /input-dir```

-step 4: The following command is used to copy the input file named data_tem.txt 
in the input directory of HDFS. now you at the directory project

```$ hadoop fs -put data_tem.txt /input-dir```
```$ hadoop fs -ls /input-dir #to check it out```

-step 5: The following command is used to run the maximum_monthly_temperature
application by taking the input files from the input directory.

the program run succsessfully like this
======================================

18/03/08 15:17:46 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
18/03/08 15:17:46 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
18/03/08 15:17:47 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
18/03/08 15:17:47 WARN mapreduce.JobResourceUploader: Hadoop command-line option parsing not performed. Implement the Tool interface and execute your application with ToolRunner to remedy this.
18/03/08 15:17:47 INFO mapred.FileInputFormat: Total input files to process : 1
18/03/08 15:17:47 INFO mapreduce.JobSubmitter: number of splits:2
18/03/08 15:17:47 INFO Configuration.deprecation: yarn.resourcemanager.system-metrics-publisher.enabled is deprecated. Instead, use yarn.system-metrics-publisher.enabled
18/03/08 15:17:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1520494781626_0004
18/03/08 15:17:48 INFO impl.YarnClientImpl: Submitted application application_1520494781626_0004
18/03/08 15:17:48 INFO mapreduce.Job: The url to track the job: http://dimo:8088/proxy/application_1520494781626_0004/
18/03/08 15:17:48 INFO mapreduce.Job: Running job: job_1520494781626_0004
18/03/08 15:17:54 INFO mapreduce.Job: Job job_1520494781626_0004 running in uber mode : false
18/03/08 15:17:54 INFO mapreduce.Job:  map 0% reduce 0%
18/03/08 15:17:59 INFO mapreduce.Job:  map 100% reduce 0%
18/03/08 15:18:05 INFO mapreduce.Job:  map 100% reduce 100%
18/03/08 15:18:06 INFO mapreduce.Job: Job job_1520494781626_0004 completed successfully
18/03/08 15:18:06 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=39
		FILE: Number of bytes written=605717
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=515
		HDFS: Number of bytes written=24
		HDFS: Number of read operations=9
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=2
	Job Counters 
		Launched map tasks=2
		Launched reduce tasks=1
		Data-local map tasks=2
		Total time spent by all maps in occupied slots (ms)=7359
		Total time spent by all reduces in occupied slots (ms)=2723
		Total time spent by all map tasks (ms)=7359
		Total time spent by all reduce tasks (ms)=2723
		Total vcore-milliseconds taken by all map tasks=7359
		Total vcore-milliseconds taken by all reduce tasks=2723
		Total megabyte-milliseconds taken by all map tasks=7535616
		Total megabyte-milliseconds taken by all reduce tasks=2788352
	Map-Reduce Framework
		Map input records=5
		Map output records=5
		Map output bytes=45
		Map output materialized bytes=45
		Input split bytes=188
		Combine input records=5
		Combine output records=3
		Reduce input groups=3
		Reduce shuffle bytes=45
		Reduce input records=3
		Reduce output records=3
		Spilled Records=6
		Shuffled Maps =2
		Failed Shuffles=0
		Merged Map outputs=2
		GC time elapsed (ms)=273
		CPU time spent (ms)=2220
		Physical memory (bytes) snapshot=792772608
		Virtual memory (bytes) snapshot=5907824640
		Total committed heap usage (bytes)=551026688
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=327
	File Output Format Counters 
		Bytes Written=24
============================================

-step 6: check file output and show file output part-00000

```$ hadoop fs -ls /output-dir/```
```$ hadoop fs -cat /output_dir/part-00000```

-step 7: to move file output part-00000 from HDFS to local

```$ hadoop fs -get /output-dir/part-00000 /path/to/local/file```
 
