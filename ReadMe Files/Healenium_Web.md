# Healenium
## Self-healing library for Selenium Web-based tests

## Set-Up

### 1. Install docker by the given url in your local 
URL - https://docs.docker.com/desktop/install/windows-install/

### 2. Create a maven project 


### 3. Add the Maven dependency in the pom.xml file of the automation framework


for Maven projects:
 ```
 <dependency>
	<groupId>com.epam.healenium</groupId>
	<artifactId>healenium-web</artifactId>
	<version>3.4.4</version>
</dependency>
 ```
### 4. Init driver instance of SelfHealingDriver (wrapping your Selenium driver with SelfHealingDriver)
```
//declare delegate
WebDriver delegate = new ChromeDriver();
//create Self-healing driver
SelfHealingDriver driver = SelfHealingDriver.create(delegate);
```
### 5. Specify custom healing config file healenium.properties under test/resources directory, ex.:

```
recovery-tries = 1
score-cap = 0.5
heal-enabled = true
serverHost = localhost
serverPort = 7878
imitatorPort = 8000
```
recovery-tries - list of proposed healed locators

heal-enabled - flag to enable or disable healing. Also you can set this value via -D or System properties, for example to turn off healing for current test run: -Dheal-enabled=false

score-cap - score value to enable healing with predefined probability of match (0.5 means that healing will be performed for new healed locat	ors where probability of match with target one is >=50% )

serverPort - ip:port or name where hlm-backend instance is installed

imitatorPort - ip:port or name where imitate instance is installed

### 6. Add Plugins for Reporting in the pom.xml file
```
    <plugins>
			<plugin>
				<groupId>com.epam.healenium</groupId>
				<artifactId>hlm-report-mvn</artifactId>
				<version>1.1</version>
				<executions>
					<execution>
						<id>hlmReport</id>
						<phase>compile</phase>
						<goals>
							<goal>initReport</goal>
						</goals>
					</execution>
					<execution>
						<id>hlmReportB</id>
						<phase>test</phase>
						<goals>
							<goal>buildReport</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
		</plugins>
```
## Start the healenium backend
### Step 1 - Create a folder in the root folder of the framework and create the docker-compose file under this folder
$ curl https://raw.githubusercontent.com/healenium/healenium-client/master/example/docker-compose.yaml -o docker-compose.yaml
### Step 2 - Create /db/sql folder on the same level in your project. Add init.sql file into ./db/sql/init.sql folder in your project.
$ curl https://raw.githubusercontent.com/healenium/healenium-client/master/example/init.sql -o init.sql
```
|__infra
    |__db/sql
        |__init.sql
    |__docker-compose.yml
|__src/main/java/
|__src/test/java/
|__pom.xml
```
### Step 3 - Start the Docker by using the below command under folder in which docker compose file is storied.
Docker compose up -d

### Step 4 - Run the framework with the same command like normal example :
mvn clean test

### Step 5 - After test execution you should see generated report link in command line logs.
Report contains only healed locators with old-new values and a button that tells if healing was successful for further algorithm corrections.
Report Link Example: "http://localhost:7878/healenium/report/8cc17ac3-c346-43e9-917d-b2acc9ca07db"


### 7. Run commands on root directory to read the Healenium database :

### Step 7.1 List of active containers, including their container IDs, image names, status, ports, and other information.
docker ps 

### Step 7.2 Execute shell file of database(infra-db-1).
docker exec -it postgres-db sh

### Step 7.3 This is a PostgreSQL command-line utility (psql) used to connect to a PostgreSQL database. "healenium_user" is username and "healenium" is database name
psql -U healenium_user -d healenium

### Step 7.4 list all tables in the current database
\dt *.*

### Step 7.5 Display all the data from the healing_result table
select * from healenium.healing_result;

### Step 7.6 Stored success data
select * from healenium.healing;

