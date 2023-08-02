## FOSSA workflow for inbound use of packages

### Goal of this repository
These are the recommended steps in how to use FOSSA for the approving/disapproving a package for inbound usage. FOSSA does _NOT_ recommend scanning the OSS libraries as actual projects. The intention here is that source code is scanned for OSS licenses, so packages for inbound usage should be scanned the same way as you would scan your projects.
Here are the following steps to complete the process with your OSPO lead:

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
  - Make sure an "inbound usage" [label](https://docs.fossa.com/docs/projects-ui-whats-new#labels) exists in FOSSA.

### Support
If you were brought here by your OSPO lead and/or from your FOSSA Customer success team, please reach out to them for feedback/and questions.
