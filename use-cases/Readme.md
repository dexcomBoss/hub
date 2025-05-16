# Clinical Hub Requirements

## Study Management

### 1. Create Study
**Requirement:** The app shall allow a user to create a new clinical study with the following:
- a unique name 
- description 
- duration
- data collection frequency
- participant thresholds
- selected study-specific metrics.

**Details:**
- Study name must be unique within the site
- Data collection frequency must be within valid ranges (e.g., every 5 minutes, every hour, 1 week)
- Study-specific metrics must be selected from a pre-defined list
- Study Admin must be logged into Clinical Hub app
- New study is created with specified parameters upon successful validation

**Source:** UC-1 Create Study

### 2. Search Studies
**Requirement:** The app shall provide a search bar that allows users to search for studies by:
- Study name
- Study ID
- Site ID
- Status (active/inactive)
- Date range
- Participant count

**Details:**
- Search results must update in real-time as user types
- Search must support partial matches
- Search must be case-insensitive
- Results must be sortable by any searchable field
- Search history must be maintained for quick access
- Search must support advanced filtering options
- Results must display key study information at a glance
- Search must be accessible from any study management screen

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

**Filter Management:**
- Filters must be combinable using AND/OR logic
- Filter combinations must be savable as presets
- Filter presets must be shareable with other users
- Filters must be exportable for reporting
- Filter history must be maintained
- Filters must be resettable to defaults
- Filter changes must be undoable

**Source:** UC-1 Create Study

### 1.1 Study Parameter Defaults
**Requirement:** The app shall provide default values for study parameters as follows:

#### General Study Parameters

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| Study_ID | Represents the study ID provided for the participants | Up to 16 characters including letters, digits, and special characters<br>Examples: "PTL-1000353S002", "IIS-2021-056", "OUS 2020-027" | N/A | Mandatory |
| Study_name | Unique identifier for the study | Must be unique within the site | N/A | Mandatory |
| Site_ID | Represents the Site ID provided for the participants | Positive integer, up to 3 digits (leading zeros acceptable) | N/A | Mandatory |
| Sensors_Max | Maximum number of sensors a participant can pair with in a trial | Positive integer up to 7 sensors | 6 | Optional |
| Contact_Instructions | Message displayed to participants in the contact screen | Up to 500 characters including letters, digits, and special characters | "Find study staff contact information in your participant instructions." | Optional |

#### Sensor Configurations

##### G7 Logger Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "logger" | N/A | Mandatory |
| background_upload | Hours until background upload | Non-negative integer (hours), 0 means no auto download | N/A | Mandatory |
| pstat_high | Upper bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| pstat_low | Lower bound for current readings | Any integer (Low < High) | N/A | Mandatory |
| temp_high | Upper bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| temp_low | Lower bound for temperature | Any integer (Low < High) | N/A | Mandatory |
| session_duration | Session length in hours | Non-negative integer (unlimited) | 360 | Optional |

##### G7 Commercial Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "g7 commercial" | N/A | Mandatory |
| upload_freq | Upload frequency in hours | Non-negative integer (unlimited) | 24 | Optional |

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
| session_duration | Session length in hours | Non-negative integer (unlimited) | 360 | Optional |
| upload_freq | Upload frequency in hours | Non-negative integer (unlimited) | 24 | Optional |

##### D1G7 Sensor

| Parameter | Description | Validation | Default | Status |
|-----------|-------------|------------|---------|--------|
| type | Sensor type identifier | Must exactly match "d1g7" | N/A | Mandatory |
| upload_freq | Upload frequency in hours | Non-negative integer (unlimited) | 24 | Optional |

**Details:**
- Defaults must be clearly visible during study creation
- Defaults must be easily modifiable
- Defaults must be validated against study requirements
- Defaults must be configurable by system administrators
- Defaults must be documented in the study creation interface
- Sensor configurations must be validated against manufacturer specifications
- Temperature and current reading bounds must be enforced for data quality
- Upload frequencies must be configurable based on study requirements
- All mandatory fields must be provided during study creation
- Optional fields will use defaults if not specified

**Source:** UC-1 Create Study

### 3. Set Study Parameters
**Requirement:** The app shall allow the Study Admin to set the study duration, data collection frequency.

**Details:**
- Data collection frequency must be within valid ranges
- Participant thresholds must be reasonable and configurable
- Changes must be validated before implementation

**Source:** UC-1 Create Study

## Participant Management



### 5. Manage Study
**Requirement:** The app shall allow the Study Admin to add, modify, and remove study sites for the study. (check with Bethan)

**Details:**
- Site names must be unique within study
- Site configuration must be validated
- Site status tracking required

**Source:** UC-5 Manage Study Sites



### 6. Monitor Compliance
**Requirement:** The app shall provide participant compliance and engagement with the following information: 
- sensor wear time (total amount of time participant has been wearing)
- last uploads from each participant
- data uploads missed / total uploads (study completion metric) (data capture rate) (check with Bethany)
- start day and last day for each participant
- drill down to troubleshoot more information about participant (firmware, last connection status, display device info, device model, Tx software number, Tx firmware number) (log if they did retry)
- active wearables / expected wearables

**Details:**
- Real-time compliance tracking
- Multiple compliance metrics
- Automated alerts for non-compliance
- Historical compliance data access

**Source:** UC-3 Monitor Study Health

### 7. Export Data
**Requirement:** The app shall allow an admin to export collected study or site data in the following formats:
- CSV
- JSON
- Excel


**Details:**
Kind of data from Accountability Log Various types of reports
Accountability Log
site id, participant number, sensor number, pairing code, sensor insertion, app insertion date, sensor stop date
$$$ Check with Bethany

**Source:** UC-7 Export Data


### 8. Send Remote Commands
**Requirement:** The app shall allow the Study Admin to send secure remote commands to a participant's Clinical App:
- stop specific sensor
- stop all sensors
- force connect ??? $$$ check with Bethany
- end a study for participant


**Details:**
- Secure command transmission
- Rate limiting (1 command/minute/participant)
- Command confirmation required
- Command history tracking
- Error handling for failed commands
- Ideally when drilling down to participant

**Source:** UC-6 Send Remote Command

### 9. Configure Consent
**Requirement:** The app shall allow an admin to configure their terms of service, usage, and technical support.

**Details:**
- Clear consent options
- Easy consent management
- Consent history tracking
- Real-time consent status updates
- Consent documentation

**Source:** UC-9 Manage Consent

## Survey Management

### 10. Configure Surveys
**Requirement:** The app shall allow the Study Admin to configure and manage study-specific surveys and questionnaires.

**Details:**
- Survey template management
- Question customization
- Response validation
- Survey scheduling
- Response tracking

**Source:** UC-8 Survey Configure



### 11. Monitor Sensor Status
**Requirement:** The app shall monitor and display sensor connectivity status to the Study Admin, generating alerts for disconnections and enabling remote troubleshooting.

**Details:**
- Real-time status monitoring
- Automated alerts
- Remote troubleshooting capabilities
- Status history tracking
- Performance metrics

### 12. Generate Audit Trails
**Requirement:** The app shall generate and provide access to audit trails for all app activities to the Full Admin.

**Details:**
- Comprehensive activity logging
- Secure audit trail storage
- Access control for audit data
- Export capabilities
- Search and filter functionality





### 15. Generate Regulatory Documentation
**Requirement:** The app shall allow the Study Admin to generate regulatory documentation for serious adverse events (SAEs) and other compliance requirements.

**Details:**
- Standardized templates
- Automated data population
- Version control
- Approval workflow
- Export capabilities

### 19. Logging
**Requirement:** The app shall allow the Site Admin to log and track adverse events reported through the Clinical App.

**Details:**
- Capture event details
- Record severity levels
- Document follow-up actions
- Generate automated alerts
- Maintain event history

