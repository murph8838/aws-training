#Services
## Data
### Kinesis
 - Streaming data analytics
 - Maybe comparable to log rocket?

## Monitoring
### CloudWatch
 - App monitoring - kinda like AppDynamics

## Processing
### Lambda
 - significant chunk of free processing
 - Permission to execute Lambda from Connect is not granted by default when a function is created. You have to create the appropriate permissions from the CLI (the admin guide contains details on how to do this)

## Speech
### Lex
 - Speech to text
 - natural language processing (identify intent)
### Polly
 - Text to speech (natural sounding speech)
 - Used frequently for "ambush" messages (rapid turnaround, not enough time for legit production/legal stuff)

## Storage
### S3 (Simple Storage Service)
 - active use storage
 - region-aware
 - object store
 - 11 9s available
 - scalable
 - Can host simple web pages
### Glacier
 - Long term cold storage
### DynamoDB
 - KVP Storage

## Security
### Directory Service
### IAM (Identity and Access Management)

# Amazon Connect 
## Random
 - Skill == Queue
 - Customize call flow based on user profiles (assuming this can be determined by caller location if unknown?)
 - Voice talent can be uploaded, polly can be used, recorder available
 - Users == Agents
 - SAML - Single sign-on capability; incorporates corporate identity with amazon connect
 - DNIS Table can be used to dynamically configure modules, and hypothetically you could provide a configuration interface to business partners, so they can manage what modules are enabled (there is much more to this than I captuerd, but I'd need to research more to understand it)
 - Connect doesn't support versioning, so make sure to export flows, version them, and import to activate
   - Treat your connect instance as prod, and deploy changes from SCM

### Routing Profiles
 - Add priorities routing queues, and can assign delays to allow for higher priority agents to take calls before lower priority agents
 - For example, you can assign a spanish speaking agent to priority 1, 0 delay spanish queue, but if they also speak english, you can assign them as priority 2, 30 second delay to an english queue. This means if a customer is waiting >30 seconds on the english queue, the spanish agent can then be assigned
### Security Profiles
 - Can add/edit/remove
### Phones
 - Can configure soft phone vs desk phone
 - Can assign, at agent level, after call work alotment
 - Auto-accept
### Agent Hierarchies
 - Can configure hierarchies for agent reporting independent of queues
### Quick Connects
 - rapid transfer options for agents when in call
 - Can be specific agents, queues, other flows, or outside calls(?)
 - warm transfers (original connector can stay on the line)
 - example, transfer a customer to a separate, non-recorded flow, for a secure conversation, and configure the quick-connect to keep the original agent on hold, so the call can come back to the same agent after the secure session is done
### Metrics
 - View dashboards for queues, agents, flows
 - Allows viewing time ranges, filtered info, specific metrics
 - Allows for saving, sharing of report configurations
### Contact Flows
 - Drag and drop call flow programming
 - Flows can transfer to queues, other flows, etc.
   - transfering between flows allows module flow configuration
   - Flow transfers allow insertion of logic (conditions for transfer)
 - Supports A/B and Canary type configurations (but not sure how to set it up)
 - Also supports distribution by customer attributes
 - Can wire in lambda functions to perform actions that aren't available as out-of-the-box widgets

## Other relevant things
 - Training available for good AWS Practices
