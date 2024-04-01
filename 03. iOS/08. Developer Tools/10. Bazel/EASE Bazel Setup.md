##### `bazelw` wrapper script

It has its own wrapped script named `.bazelw` in root. This script in fact dowloads Bazelisk if needed (the Bazelisk version is specified within the script), saves it in `/Bazel/tmp/bazel/versions` , installs some Java certs (why and what are those), and then runs the downloaded Bazelisk exec passing it all the arguments the script had received.

> What is happening in the 'Install the java certs' part in the script.

##### Bazel config files

`.bazelversion` - Does have this file to specify the Bazel version to use.

`.bazelrc` - Bazel related config variables
