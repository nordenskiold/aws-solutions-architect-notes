## Simple Workflow Service  (SWF)

### Overview
SWF is a web service that makes it easy to coordinate work across distributed application components. SWF enables applications for a range of use cases, including media processing, web application back-ends, business process workflows, and analytics pipelines, to be designed as a coordination of tasks. The tasks represent invocations of various processing steps in an application which can be performed by executable code, web service calls, human actions, and scripts.

#### SWF Actors
- **Workflow Starters** - An application that can initiate a workflow. E.g. Amazon.com after a placement of an order is submitted
- **Deciders** - Controls the flow of activity tasks in a workflow execution. If something has finished or failed in a workflow, a *Decider* decides what to do next
- **Activity Workers** - Carries out the activity tasks

#### SQS vs. SWF

|                   | SQS | SWF  |
| -------------- |:-- --:| -------:|
| Retention  | Up to 14 days | Up to 1 year |
| API      | Message-oriented API  |   Task-oriented API |
| Duplication      | You need to handle duplicated messages and/or ensure that a message is processed only once |   Ensures that a task is assigned only once and never duplicated |
| Tracking      | Requires you to implement your own application-level tracking, especially if your application uses multiple queues  |  Keeps track of all the tasks and events in an application |

### Key Take Aways
- SQS is pull based, not pushed based