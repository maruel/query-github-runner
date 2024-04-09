# Query GitHub Runner

This repository defines a workflow that queries a lot of information from the
running environment. This help understanding the differences in behavior on the
runner versus a local environment.

While https://github.com/actions/runner-images provides information about the
base image, it doesn't contain the sources of
`c:\actions\runner-provision-Windows\provisioner.exe`

See recent actions at
https://github.com/maruel/query-github-runner/actions/workflows/query_windows.yml
to see the output of the workflow.

![screenshot.png](screenshot.png)
