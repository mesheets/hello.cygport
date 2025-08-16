Cygwin Cygport Workflow Template
================================
A template repository preconfigured to automatically build Cygwin Cygport files.

About the Cygwin Cygport Workflow Template
------------------------------------------
The [Cygwin Cygport Workflow Template](https://github.com/mesheets/Cygport-Workflow-Template)
is designed to automatically generate
[Cygwin Cygport packages](https://cygwin.com/packaging-contributors-guide.html)
for `*.cygport` file(s) contained in the root of the repository.

Basic Usage Info
----------------
Any Cygwin Cygport files (with a `*.cygport` extension) created within the root
directroy will be automatically build for all supported architectures
(currently “x86” and “x86_64”) by a GitHub Workflow upon a push, a pull
request, or a manual workflow invocation request.

How to Keep Current with the Parent Template
--------------------------------------------
By completing a few additional steps, any repositories created from this
template can be configured to check for updates to the original template
repository.
* Checks weekly by default, or can also be invoked manually
* If updates are found, the changes are posted as a pull request
* If during a subsequent run additional changes are found but an unapplied
  pull requests with updates is still pending, the old pull request will be
  removed and replace with a single new pull request that combines all
  pending updates.
* Neither this README.md file nor any files added to a repository created from
  this template will be impacted by this template synchronization process.
  (Feel free to replace this README.md with your own project-specific one.)

Steps to Enable the Template Update Synchronization
---------------------------------------------------
For general template synchronization senarios, modifying the repository
settings as follows is usually sufficient:
* Navigate to 
Settings > Code and Automation > Actions > General > Workflow Permissions
* Check “Allow GitHub Actions to create and approve pull requests”

**_However_**, automated updating of workflow files requires additional permissions,
so the following steps are necessary instead:

 1. Create a Fine-Grained Personal Access Token (or similar)
    + Navigate to Profile Icon > Settings > Developer Settings (at the bottom) > Personal Access Tokens > Fine-Grained Tokens
 2. Click the “Generate New Token” button
 3. Give the token a name and (optionally) a description
 4. Specify a token expiration date
 5. At a minimum, select “only” the repositories created from this template repository
 6. Define token permissions as follows:
 
    | Permission Type | Permission Level |
    | --------------- | ---------------- |
    | Metadata        | Read             |
    | Contents        | Read & Write     |
    | Pull Requests   | Read & Write     |
    | Workflows       | Read & Write     |
 
 7. Click the “Generate Token” button when ready
 8. Capture a copy of the token that has been generated
 9. Create a “Secret” that can be used to reference this token
    + In the child repository generated from the template, nativate to
	  Settings > Secrets & Variables > Actions > Repository Secrets
10. Click the “New Repository Secret” button
11. Define the Secret Name as “**CYGPORT_TEMPLATE_SYNC_TOKEN**” (without the quotes)
12. Paste the token generated earlier into the “Secret” field
13. Click the “Add Secret” button
14. To verify, manually run the “Template Synchronizer” workflow.  It should
    automatically detect the existence of the CYGPORT_TEMPLATE_SYNC_TOKEN and
	then check the parent template for updates.

For troubleshooting information, you may also refer to
[this link](https://github.com/marketplace/actions/actions-template-sync#troubleshooting).

Example Repositories
--------------------
Refer to the following for example usage of this template:
* [GNU Hello Cygport Package](https://github.com/mesheets/hello.cygport)
