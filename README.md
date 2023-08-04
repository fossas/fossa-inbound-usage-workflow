## FOSSA workflow for inbound use of packages

### Goal of this repository
These are the recommended steps in how to use FOSSA for the approving/disapproving a package for inbound usage. FOSSA does _NOT_ recommend scanning the OSS libraries as actual projects. The intention here is that source code is scanned for OSS licenses, so packages for inbound usage should be scanned the same way as you would scan your projects.
Here are the following steps to complete the process with your OSPO lead:

### Intended audience
These are steps that an organization's engineering team must take, should they request inbound use for particular packages. OSPO must be aware of these steps and integrate them to make the inbound usage workflow easier. It's not required of the OSPO to fulfill these steps on behalf of the requester, who may know more about the nature of using the OSS package itself. Therefore, the following recommended steps are meant for engineers/developers to go through.

### Recommended steps
- [ ] Create a new test repository, namely “inbound-usage-[ticketing-system]-[ticket-number]”.
  - For example: `inbound-usage-jira-1234`. 
  - For the repository name, ensure you have a clear name so everyone who goes into FOSSA has an idea of what the project is. To further make things clear, see the `label` step below.
- [ ] Add the OSS package as you’d normally do in your existing projects. Here are some examples:
  - If you are wanting to use a python package, then add it to a requirements.txt file.
  - If you are wanting to add a go dependency, then add it to a go.mod.
  - If you are wanting to use a maven dependency, add it to your pom.xml. 
- [ ] Look at FOSSA’s strategies for more information: https://github.com/fossas/fossa-cli/tree/master/docs/references/strategies
- [ ] Run a FOSSA scan on this test project
  - Use the FOSSA CLI in this way: “fossa analyze --label inbound-usage”
  - Make sure you have your [API token](https://docs.fossa.com/docs/api-reference).
  - Make sure an "inbound usage" [label](https://docs.fossa.com/docs/projects-ui-whats-new#labels) exists in FOSSA.
     
### Go example
This example shows how to scan `optimizely` for inbound use.

- [ ] In the GitHub UI, create a test repository called `inbound-usage-jira-20231`.
  - [ ] Or clone this repository and skip some steps.
- [ ] Add a dummy README describing the purpose of the project.
- [ ] Clone the project.
- [ ] Install Go.
- [ ] `cd` to cloned project.
- [ ] Run `go mod init fossa-inbound-usage`
- [ ] Run `go get github.com/dusan-dragon/terraform-provider-optimizely`
- [ ] Install FOSSA CLI.
- [ ] Login to FOSSA.
  - [ ] Ensure `inbound-usage` label exists. If not, contact your OSPO lead (they should be admins in FOSSA).
  - [ ] Grab your FOSSA access token.
- [ ] Run`fossa analze --label inbound-usage --fossa-api-key $FOSSA_API_KEY`
  - [ ] Feel free to use the `project` to supply a different project name.
- [ ] Visit the FOSSA Report Link that is generated in `stderr` and wait for the scan to complete.
- [ ] Review results with your OSPO.

### Support
If you were brought here by your OSPO lead and/or from your FOSSA Customer Success team (or any other cool folks at FOSSA), please reach out to them for feedback/and questions.

### FAQ
See our [wiki](https://github.com/fossas/fossa-inbound-usage-workflow/wiki/FAQ) page for self-help.
