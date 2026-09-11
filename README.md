aws-grocery-aggregator-service
☁️ Infrastructure & Deployment

This project is a RESTful backend service built with Spring Boot (Java 17) and is currently deployed on an AWS EC2 instance.

Cloud Provider: Amazon Web Services (AWS).

Instance Type: t2.micro (Ubuntu 22.04 LTS).

Networking: Configured AWS Security Groups to allow inbound traffic on Port 8080.

Process Management: Utilized nohup for background execution to ensure persistent uptime after terminal session termination.
 
🚦 API Validation

The following endpoints have been verified via Postman to ensure successful data aggregation and 200 OK status codes.

Endpoint	Method	Purpose
/products/search	GET	
Search for grocery items by name (e.g., ?name=Milk) 

/products/best-deal	GET	
Compare prices across sources to find the best deal 

/	GET	
Home/Health check endpoint 

🛠️ Technical Deployment Playbook

The following workflow was utilized to manage the remote deployment via the Linux terminal.

1. Establish Remote Connection

Securely connect to the EC2 instance using an SSH key:

Bash
ssh -i ~/Downloads/your-key.pem ubuntu@3.16.46.98
2. Environment Preparation

Ensure Port 8080 is clear before deploying a new build:

Bash
sudo fuser -k 8080/tcp
3. Build and Package

Navigate to the project root and compile the executable JAR file using the Maven Wrapper:

Bash
cd ~/GroceryPriceAggregator
./mvnw clean package
4. Background Execution

Launch the application in the background and redirect output to a log file for monitoring:

Bash
nohup java -jar target/*.jar > app.log 2>&1 &
5. Live Logs & Verification

Monitor the startup logs to verify the Spring Boot context has initialized correctly:

Bash
tail -f app.log
6. Endpoint Mapping

Verify active REST controllers and request mappings directly from the source code:

Bash
grep -rnE "@(RequestMapping|GetMapping)" src/main/java


Complete and Confident!
