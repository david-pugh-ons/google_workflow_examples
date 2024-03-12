# google_workflow_examples
Selection of Google Workflow Examples that could be used for common analysis based Google Projects such as creation and managmeent of Workbench Instances.

## Vertex AI Workbench
- extraction and standardisation of information from both V1 and V2 of the API
- creation of Workbench Instance with security setting, with optional writing of Instance details to Firestore
- hitting v1 and v2 of the API and listing all notebooks from zones a, b and c and returning a list of all instances, standardining the response form both API versions and adding these to a collection in Firestore
  being able to get information on a specific notebook, as well as stop, start and reset it - can optionally update the Firestore deocument for this instance as well as obtain info in a JSON object
  
We can call multiple projects to list all notebooks in a bigger platform by calling the listing workflow for each project in parallel, as each call is independent. For example:

```

main:
    params: [input]
    steps:
    - get_inputs:
        assign:
            - projects: ${map.get(input, "projects")}
            - firestore_project: ${map.get(input, "firestore_project")}

    - list_projects:
        parallel:
            for:
                value: project        
                in: ${projects}
                steps:
                    - get_notebooks:
                        call: googleapis.workflowexecutions.v1.projects.locations.workflows.executions.run
                        args:
                            workflow_id: workflow-list-notebooks-update-firestore
                            argument:
                                project_id: ${project}
                                firestore_collection: "user"
                                firestore_project_id: ${firestore_project} 
```

Other workflows can be called as child workflows to simplify and reuse code. The workflows listen below can be used for exmple to create teh service account used by an instance and also add bindings to allow the instance to access WIP buckets and datasets. 

## Service Accounts
 - creation of service account

## Firestore
- patching a document ina given database/collection

## BigQuery
- append/replace bindings for a given role on a dataset

## Storage
- append/replace bindings for a given role on a bucket
