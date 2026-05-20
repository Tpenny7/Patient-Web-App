# Patient Data App
This patient data app cleanly summarises and presents patient data from a csv file and allows the data to be changed and saved.
## Prerequisites

- Java 25 (as configured in `pom.xml`)
- Maven 3.9+

## Project Structure

- `src/main/java` — Java source code (including the embedded Tomcat bootstrap in `uk.ac.ucl.main.Main`)
- `src/main/webapp` — Static web resources and JSPs
- `target` — Build output (created by Maven)
- `war-file` — Packaged WAR output (created by Maven)

## Compile

Build the project and produce a WAR file:

```bash
mvn clean package
```

This writes the WAR to `war-file/`.

## Run (Embedded Tomcat)

First compile the project, then run the main class via Maven:

```bash
mvn clean compile exec:exec
```

By default the server starts on port `8080`. Open:

```
http://localhost:8080
```

## Configuration

You can configure the server using system properties or environment variables:

- `SERVER_PORT` — Port to bind (default: `8080`)
- `WEBAPP_DIR` — Web resources directory (default: `src/main/webapp/`)
- `CLASSES_DIR` — Compiled classes directory (default: `target/classes`)

Example (using environment variables):

```bash
SERVER_PORT=9090 mvn clean compile exec:exec
```

## Loading the Data File
The path of the loaded data file can be changed in the AppConfig class.
## Features
### Search
Allows the user to enter a keyword to find all records which contain this keyword
### Patient List
Presents all the patients in a list. Individual patients can be clicked on to view details about them.
### Oldest and Youngest Patient
Shows the oldest and youngest patients who have not yet died.
### Number of People in the Same Residence 
Displays the residences with the most people living in them. They must have the same address, zip, city and state. 
### Number of Patients with a Selected Attribute
Displays, in descending order, all the patients who share a particular attribute.
### Add Patient
Allows the user to add a patient. The ID is automatically generated and checking is done to ensure that all required fields are provided and in the correct format.
The new patient is saved to the csv file.
### Edit and Delete Patient
When viewing an individual patient, the user has the option to edit or delete the patient. The changes are saved to the csv file. 
