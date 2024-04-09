# Query GitHub Runner

This repository defines a workflow that queries a lot of information from the
running environment. This help understanding the differences in behavior on the
runner versus a local environment.

While https://github.com/actions/runner-images provides information about the
base image, it doesn't contain the sources of
`c:\actions\runner-provision-Windows\provisioner.exe`
