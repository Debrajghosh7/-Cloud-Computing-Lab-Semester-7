# Experiment 9: Develop MapReduce Application Using Hadoop Cluster Setup

## 📌 Aim

To set up a Hadoop cluster in a Linux environment and develop, execute and verify a MapReduce application using the Hadoop Distributed File System (HDFS) and Hadoop MapReduce framework.

## 🛠️ Technologies and Tools Used

- **Apache Hadoop:** Open-source framework for distributed storage and processing.
- **HDFS:** Hadoop Distributed File System for distributed data storage.
- **MapReduce:** Programming model for processing large datasets.
- **YARN:** Manages cluster resources and application execution.
- **Java (OpenJDK 17):** Programming language used to develop the MapReduce application.
- **Ubuntu Linux:** Operating system for Hadoop configuration.
- **OpenSSH:** Used for communication between Hadoop nodes.
- **Terminal:** Used to execute Hadoop and Linux commands.

## 📚 Experiment Overview

This experiment is divided into four major practical tasks.

### Task 1: Hadoop Cluster Setup

**Objective:** Install Java and Hadoop and configure the Hadoop environment.

**Steps Performed:**

1. Checked Java installation.
2. Installed OpenJDK 17.
3. Downloaded and installed Apache Hadoop 3.x.
4. Configured Hadoop environment variables.
5. Configured Hadoop cluster configuration files.
6. Configured SSH for passwordless localhost access.
7. Prepared a single-node pseudo-distributed Hadoop environment.

**Java Installation Commands:**

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

Verify Java installation:

```bash
java -version
javac -version
```

**Hadoop Installation Commands:**

```bash
tar -xzf hadoop-3.x.x.tar.gz
sudo mv hadoop-3.x.x /usr/local/hadoop
```

Verify Hadoop installation:

```bash
/usr/local/hadoop/bin/hadoop version
```

**Environment Variables:**

The following variables were configured in `~/.bashrc`:

```bash
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export HADOOP_HOME=/usr/local/hadoop
export HADOOP_HDFS_HOME=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
```

Apply the changes:

```bash
source ~/.bashrc
```

Verify:

```bash
echo $HADOOP_HOME
hadoop version
```

**Important Hadoop Configuration Files:**

| Configuration File | Purpose |
|---|---|
| core-site.xml | Configures the default Hadoop filesystem. |
| hdfs-site.xml | Configures HDFS storage and replication. |
| mapred-site.xml | Configures MapReduce execution. |
| yarn-site.xml | Configures YARN resource management. |
| workers | Specifies Hadoop worker nodes. |

**SSH Configuration Commands:**

```bash
sudo apt install openssh-server openssh-client -y

sudo systemctl enable --now ssh

ssh-keygen -t ed25519

cat ~/.ssh/id_ed25519.pub >> ~/.ssh/authorized_keys

chmod 600 ~/.ssh/authorized_keys

ssh localhost
```

### Task 2: HDFS Configuration and Basic Operations

**Objective:** Configure Hadoop Distributed File System and perform basic file operations.

**Steps Performed:**

1. Formatted the Hadoop NameNode.
2. Started HDFS services.
3. Started YARN services.
4. Verified running Hadoop processes.
5. Created directories in HDFS.
6. Created sample input data.
7. Uploaded the input file to HDFS.
8. Verified file storage and contents.

**Format the NameNode:**

```bash
hdfs namenode -format
```

**Start Hadoop Services:**

```bash
start-dfs.sh
start-yarn.sh
```

**Verify Running Processes:**

```bash
jps
```

Expected Hadoop processes:

- NameNode
- DataNode
- SecondaryNameNode
- ResourceManager
- NodeManager

**Create an HDFS Directory:**

```bash
hdfs dfs -mkdir -p /user/student/cloud-lab9/input

hdfs dfs -ls /user/student/cloud-lab9
```

**Create Sample Input Data:**

```bash
mkdir ~/cloud-lab9
cd ~/cloud-lab9
```

Create the input file:

```bash
cat > input.txt <<EOF
cloud computing provides scalable resources
cloud computing uses distributed systems
hadoop processes large datasets
hadoop provides distributed storage
mapreduce processes data in parallel
mapreduce is used for large scale data processing
EOF
```

Display the file:

```bash
cat input.txt
```

**Upload the File to HDFS:**

```bash
hdfs dfs -put input.txt /user/student/cloud-lab9/input/
```

Verify the upload:

```bash
hdfs dfs -ls /user/student/cloud-lab9/input

hdfs dfs -cat /user/student/cloud-lab9/input/input.txt
```

### Task 3: Develop a MapReduce Application

**Objective:** Develop a Java-based MapReduce application to count the frequency of words in a text file.

**Application Name:** Word Count MapReduce Program

**Concept of MapReduce:**

MapReduce is a distributed programming model used to process large datasets.

It consists of two major phases:

**1. Map Phase**

- Reads input data.
- Splits text into individual words.
- Generates intermediate key-value pairs.
- Assigns a value of 1 to each word.

Example:

```text
Input:
cloud computing provides scalable resources

Mapper Output:
cloud 1
computing 1
provides 1
scalable 1
resources 1
```

**2. Reduce Phase**

- Groups identical words.
- Adds their corresponding values.
- Generates the final word frequencies.

Example:

```text
Input:
cloud 1
cloud 1
cloud 1

Output:
cloud 3
```

**MapReduce Processing Flow:**

```text
Input Data
    |
    v
   HDFS
    |
    v
  Mapper
    |
    v
Intermediate Key-Value Pairs
    |
    v
Shuffle and Sort
    |
    v
  Reducer
    |
    v
  Output
    |
    v
   HDFS
```

**Steps Performed:**

1. Created a Java source file named `WordCount.java`.
2. Implemented the Mapper class to tokenize input text.
3. Implemented the Reducer class to calculate word frequencies.
4. Configured the MapReduce job.
5. Compiled the Java application using Hadoop libraries.
6. Created a JAR file for execution.

**Compilation Commands:**

Set Hadoop classpath:

```bash
export HADOOP_CLASSPATH=$(hadoop classpath)
```

Compile the Java program:

```bash
javac -classpath "$HADOOP_CLASSPATH" -d . WordCount.java
```

Create the JAR file:

```bash
jar -cvf wordcount.jar *.class
```

Verify the generated files:

```bash
ls
```

Expected file:

```text
wordcount.jar
```

### Task 4: Execute the MapReduce Application

**Objective:** Execute the Word Count application on Hadoop and verify the generated output.

**Steps Performed:**

1. Removed the previous output directory if it existed.
2. Submitted the MapReduce job to Hadoop.
3. Observed Mapper and Reducer execution.
4. Checked job completion status.
5. Verified the generated output directory.
6. Displayed the final word frequencies.
7. Compared the results with the original input data.

**Remove Previous Output:**

```bash
hdfs dfs -rm -r /user/student/cloud-lab9/output
```

**Execute the MapReduce Job:**

```bash
hadoop jar wordcount.jar WordCount \
/user/student/cloud-lab9/input \
/user/student/cloud-lab9/output
```

**Verify the Output Directory:**

```bash
hdfs dfs -ls /user/student/cloud-lab9/output
```

Expected files:

```text
_SUCCESS
part-r-00000
```

**Display the Final Output:**

```bash
hdfs dfs -cat /user/student/cloud-lab9/output/part-r-00000
```

**Example Output:**

```text
cloud       2
computing   2
hadoop      2
mapreduce   2
```

The output contains each word and its corresponding frequency. The exact output depends on the input dataset.

### Additional Practical Activities

#### A. Explore Hadoop Web Interfaces

Hadoop provides web-based interfaces to monitor cluster components.

**NameNode Web Interface:**

```text
http://localhost:9870
```

Features explored:

- HDFS overview.
- DataNodes.
- Storage information.
- File system information.

**ResourceManager Web Interface:**

```text
http://localhost:8088
```

Features explored:

- Applications.
- Cluster metrics.
- Nodes.
- Application status.

#### B. Examine HDFS File Blocks

Execute:

```bash
hdfs fsck /user/student/cloud-lab9/input/input.txt -files -blocks
```

Information observed:

- File size.
- Number of blocks.
- Block information.
- DataNode information.

#### C. Perform Basic HDFS Operations

List files:

```bash
hdfs dfs -ls /user/student/cloud-lab9/input
```

Display file contents:

```bash
hdfs dfs -cat /user/student/cloud-lab9/input/input.txt
```

Download a file from HDFS:

```bash
hdfs dfs -get /user/student/cloud-lab9/input/input.txt downloaded.txt
```

Verify downloaded content:

```bash
cat downloaded.txt
```

Delete a test file (after completing the required observations):

```bash
hdfs dfs -rm /user/student/cloud-lab9/input/input.txt
```

#### D. Stop Hadoop Services

Stop YARN:

```bash
stop-yarn.sh
```

Stop HDFS:

```bash
stop-dfs.sh
```

Verify the running processes:

```bash
jps
```

## 📸 Screenshots and Practical Demonstration

The following screenshots can be included to demonstrate successful completion of the experiment:

1. Java installation and version verification.
2. Hadoop installation and version verification.
3. Hadoop environment variable configuration.
4. Hadoop configuration files.
5. SSH passwordless localhost connection.
6. NameNode formatting.
7. Hadoop services running using `jps`.
8. HDFS directory creation.
9. Sample input file creation.
10. Successful file upload to HDFS.
11. WordCount.java source code.
12. Successful Java compilation.
13. Generated wordcount.jar file.
14. Successful MapReduce job execution.
15. MapReduce output displayed from HDFS.
16. NameNode web interface.
17. ResourceManager web interface.
18. HDFS file block information.
19. Hadoop services stopped successfully.

## 🎯 Learning Outcomes

After completing this experiment, the following concepts were understood:

- Fundamentals of Apache Hadoop.
- Hadoop cluster architecture and components.
- Installation and configuration of Java and Hadoop.
- HDFS architecture and distributed file storage.
- Basic HDFS file and directory operations.
- Role of NameNode and DataNode.
- Role of YARN in resource management.
- Development of Java-based MapReduce applications.
- Working of Mapper and Reducer.
- Shuffle and Sort operations.
- Execution of MapReduce jobs.
