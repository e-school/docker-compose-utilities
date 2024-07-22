<b>Getting started with the Splunk Docker Image</b>


1. Sign up for a Docker ID at Docker Hub (Optional)

2. Download and install Docker on your system.

3. Open a shell prompt or Terminal window. 

4. Enter the following command to pull the Splunk Enterprise version 7.0.3 image. 

5. docker pull splunk/splunk 

6. Run the Docker image.

7. docker run -d -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_USER=root" -p "8000:8000" splunk/splunk 

8. Access the Splunk instance with a browser by using the Docker machine IP address and Splunk Web port. 
   For example, ``http://localhost:8000`

<b>Ports</b>
This Docker container exposes the following network ports:

- 8000/tcp - Splunk Web interface 
- 8088/tcp - HTTP Event Collector 
- 8088/tcp - Splunk Services 
- 8191/tcp - Application Key Value Store 
- 9997/tcp - Splunk receiving Port (not used by default) typically used by the Splunk Universal Forwarder 
- 1514/tcp - Network Input (not used by default) typically used to collect syslog TCP data