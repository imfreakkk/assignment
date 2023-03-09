# assignment
Python code for SSH and execute commands 

1.	Importing necessary libraries
2.	The first few lines of the code import the necessary libraries required for the application to work. Flask is used to create the web application, boto3 is used to connect to AWS services, and paramiko is used to connect to EC2 instances over SSH.
3.	Defining EC2 instance details
4.	The next section of the code defines the EC2 instance details, including the instance ID and the key pair file. This is used to establish a connection with the EC2 instance.
5.	Connecting to AWS
6.	The code then creates a session using the boto3 library, which is authenticated using the AWS access key ID and secret access key. The region name is also specified. This session is used to connect to the EC2 instance.
7.	Connecting to the EC2 instance over SSH
8.	The paramiko library is used to connect to the EC2 instance over SSH. The RSAKey.from_private_key_file() method is used to read the private key file, and the SSHClient() method is used to create an SSH client. The set_missing_host_key_policy() method is used to set the policy for automatically adding missing host keys to the client. The connect() method is then called to connect to the EC2 instance using the public IP address, the username ec2-user, and the private key.
9.	Creating a Flask application
10.	The next section of the code creates a Flask application, which can handle HTTP requests.
11.	Defining the index route
12.	The index() function is defined as the route handler for the root URL. If the request method is POST, the value of the command parameter is obtained from the request, and the exec_command() method of the SSH client is used to execute the command on the EC2 instance. The output of the command is returned 



cpu_info=$(ps aux --sort=-%cpu | awk '{if(NR==4) print $11,$3,$4,$6,$2}' ) This line retrieves the third most CPU consuming process by running the ps command with the aux option to show all processes with more detailed information, and sorting the output by CPU usage. Then the awk command is used to print the 11th, 3rd, 4th, 6th and 2nd fields of the fourth line, which contains the third most CPU consuming process. The output is then stored in the cpu_info variable.

mem_info=$(ps aux --sort=-%mem | awk '{if(NR==4) print $11,$3,$4,$6,$2}') This line retrieves the third most memory consuming process by running the ps command with the aux option to show all processes with more detailed information, and sorting the output by memory usage. Then the awk command is used to print the 11th, 3rd, 4th, 6th and 2nd fields of the fourth line, which contains the third most memory consuming process. The output is then stored in the mem_info variable.

echo "Process Name % CPU used % Memory used PORT PID" > output.txt This line creates a new file called output.txt and writes the header "Process Name % CPU used % Memory used PORT PID" to the file.

echo $cpu_info >> output.txt This line appends the cpu_info variable, which contains the third most CPU consuming process information, to the output.txt file.

echo $mem_info >> output.txt This line appends the mem_info variable, which contains the third most memory consuming process information, to the output.txt file.


