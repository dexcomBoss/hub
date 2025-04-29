# Clinical Hub Requirements

## Study Management

### 1. Create Study
The app shall allow a user to create a new clinical study with the following:
- a unique name 
- description 
- duration
- data collection frequency
- participant thresholds
- selected study-specific metrics

### 2. Search Studies
The app shall provide a search bar that allows users to search for studies by:
- Study name
- Study ID
- Site ID
- Status (active/inactive)
- Date range
- Participant count

**Filtering Capabilities:**
The app shall provide the following filtering options:
1. Study Status
   - Active
   - Inactive
   - Draft
   - Completed
   - Archived

2. Time Period
   - Start date range
   - End date range
   - Duration range
   - Last modified date

3. Participant Metrics
   - Total participant count range
   - Active participant count range
   - Compliance rate range
   - Dropout rate range

4. Sensor Configuration
   - Sensor type
   - Number of sensors per participant
   - Upload frequency range
   - Data collection frequency

5. Study Type
   - Clinical trial
   - Observational study
   - Research study
   - Pilot study

6. Data Collection
   - Data completeness percentage
   - Last data upload date
   - Data quality score
   - Missing data threshold

7. Location
   - Site location
   - Region
   - Country
   - Time zone

### 1.1 Study Parameter Defaults
The app shall provide default values for study parameters as follows:

#### General Study Parameters

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| Study_ID | Represents the study ID provided for the participants | Up to 16 characters including letters, digits, and special characters | N/A | Mandatory |
| Study_name | Unique identifier for the study | Must be unique within the site | N/A | Mandatory |
| Site_ID | Represents the Site ID provided for the participants | Positive integer, up to 3 digits | N/A | Mandatory |
| Sensors_Max | Maximum number of sensors a participant can pair with in a trial | Positive integer up to 7 sensors | 6 | Optional |
| Contact_Instructions | Message displayed to participants in the contact screen | Up to 500 characters | "Find study staff contact information in your participant instructions." | Optional |

#### Sensor Configurations

##### G7 Logger Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "logger" | N/A | Mandatory |
| background_upload | Hours until background upload | Non-negative integer | N/A | Mandatory |
| pstat_high | Upper bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| pstat_low | Lower bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| temp_high | Upper bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| temp_low | Lower bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| session_duration | Session length in hours | Non-negative integer | 360 | Optional |

##### G7 Commercial Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "g7 commercial" | N/A | Mandatory |
| upload_freq | Upload frequency in hours | Non-negative integer | 24 | Optional |

##### Proton Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "proton" | N/A | Mandatory |
| first_delay | Hours until first upload | Non-negative integer (capped at 24) | 24 | Optional |
| download_freq | Download frequency in hours | Non-negative integer (capped at 24) | 2 | Optional |
| pstat_high | Upper bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| pstat_low | Lower bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| temp_high | Upper bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| temp_low | Lower bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| session_duration | Session length in hours | Non-negative integer | 360 | Optional |
| upload_freq | Upload frequency in hours | Non-negative integer | 24 | Optional |

##### D1G7 Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "d1g7" | N/A | Mandatory |
| upload_freq | Upload frequency in hours | Non-negative integer | 24 | Optional |

### 3. Set Study Parameters
The app shall allow the Study Admin to set the study duration, data collection frequency.

## Participant Management

### 5. Manage Study
The app shall allow the Study Admin to add, modify, and remove study sites for the study.

### 6. Monitor Compliance
The app shall provide participant compliance and engagement with the following information: 
- sensor wear time
- last uploads from each participant
- data uploads missed / total uploads
- start day and last day for each participant
- drill down to troubleshoot more information about participant
- active wearables / expected wearables

### 7. Export Data
The app shall allow an admin to export collected study or site data in the following formats:
- CSV
- JSON
- Excel

### 8. Send Remote Commands
The app shall allow the Study Admin to send secure remote commands to a participant's Clinical App:
- stop specific sensor
- stop all sensors
- force connect
- end a study for participant

### 9. Configure Consent
The app shall allow an admin to configure their terms of service, usage, and technical support.

## Survey Management

### 10. Configure Surveys
The app shall allow the Study Admin to configure and manage study-specific surveys and questionnaires.

### 11. Monitor Sensor Status
The app shall monitor and display sensor connectivity status to the Study Admin, generating alerts for disconnections and enabling remote troubleshooting.

### 12. Generate Audit Trails
The app shall generate and provide access to audit trails for all app activities to the Full Admin.

### 15. Generate Regulatory Documentation
The app shall allow the Study Admin to generate regulatory documentation for serious adverse events (SAEs) and other compliance requirements.

### 19. Logging
The app shall allow the Site Admin to log and track adverse events reported through the Clinical App. 
