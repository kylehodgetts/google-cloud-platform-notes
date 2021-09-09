# IAM Breakdown

## Resource Hierarchy

- Resource
    - Something you create in GCP
- Project
    - Container for set of related resources
- Folder
    - Contains any number of sub-folders and projects
- Organization
    - Tied to G Suite or Cloud Identity domain

Default service accounts let you interact with things inside the same project by default

## Permissions and Roles

### Permissions

- Allows you to perform a certain action
- Each one follows the form `Service.Resource.Verb`
- Usually corresponds to REST API methods
- E.g.
    - [`pubsub.s](http://pubsub.su)ubscriptions.consume`
    - `pubsub.topics.publish`

### Roles

- Collection of Permissions to use or manage GCP resources
    - Admins role has ALL permissions
- Primitive Roles
    - Project level and often too broad
    - Viewer is read-only
    - Editor can view and change things
    - Owner can also control access and billing
- Predefined roles - Give granular access to specific GCP resources
    - E.g. roles/bigquery.dataEditor, roles/pubsub.subscriber
    - Read through list of roles for each product and think about why each one exists
- Custom Roles - Project or Org Level collection you define of granular permissions

## Members and Groups

### Members

- Someone is a google known identity
- Each member identified by unique email address
- Can be:
    - `user:` specific google account
        - G suite, cloud identity, gmail or validated email
    - `serviceAccount`: Service account for apps or services
    - `group`: Google group of users and service accounts
    - `domain`: Whole domain managed by G suite or Cloud Identity
    - `allAuthenticatedUsers`: Any google account or service account
    - `allUsers`: Anyone on the internet (public)

### Groups

- Google group is a named collection of Google Accounts and Service Accounts
- Every group has a unique email address that is associated with the group
- never act as the group
    - Membership in a group can grant capabilities to individuals
- Use them for everything!
- Can be used for owner when within an org
- Can nest groups in an org
    - E.g. one group for each department, all those in group for all staff

## Policies

- Binds Members to Roles for some scope of resources
- Who can do what to which thing(s)?
- Attached to some level in the Resource Hierarchy
    - Org, Folder, Project, Resource
- Roles and Members listed in policy, but Resources identified by attachment
- Always additive ("Allow") and never subtractive (no "Deny")
    - Child policies cannot restrict access granted at a higher level
- One policy per resource
- Max 1500 member bindings
    - Really high number
    - Use groups instead!
- Usually takes less than 60s to apply changes
- May take up to 7 minutes for changes to fully propagate across the system

### Managing Policy Bindings

- ❌ Can use get-iam-policy , edit json/yaml and set-iam-policy back
- ✅ Use add-iam-policy-binding and remove-iam-policy-binding
    - Are atomic operations
    - less work to do and less error prone
    - Avoids race conditions