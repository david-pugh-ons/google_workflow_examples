# google_workflow_examples
Selection of Google Workflow Examples that could be used for common analysis based Google Projects such as creation and managmeent of Workbench Instances.

## Vertex AI Workbench
- creation of Workbench Instance with security setting, with optional writing of Instance details to Firestore
- hitting v1 and v2 of the API and listing all notebooks from zones a, b and c and returning a list of all instances, standardining the response form bothe API versions and adding these to a collection in Firestore
  being able to get information on a specific notebook, as well as stop, start and reset it - can optionally update the Firestore deocument for this instance as well as obtain info in a JSON object

## Service Accounts
 - creation of service account

## Firestore
- patching a document ina given database/collection

## BigQuery
- append/replace bindings for a given role on a dataset

## Storage
- append/replace bindings for a given role on a bucket
