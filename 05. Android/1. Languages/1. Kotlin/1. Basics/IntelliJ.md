#### IntelliJ Plugins

Plugins extend the editor in various ways. A few come pre-installed, and rest can be installed from Marketplace as needed. The list is accessible using 'Settings > Plugins'. 

Official documentation [link](https://www.jetbrains.com/help/idea/managing-plugins.html#g990kh_72)

![](assets/Pasted%20image%2020240624115512.png)
Its also possible to install plugins from local files, as well as command line.

##### Marking plugins as 'required'

Certain plugins can be marked as 'required'. This can be done from 'Settings > Build, Execution, Deployment > Required Plugins'. 

> But looks like this applies for all projects, and can't be done for specific projects.

![](assets/Pasted%20image%2020240624120347.png)
#### Build Systems

While creating a new Kotlin project, the build system too needs to be selected. Note that apart from Maven, and Gradle, it also has IntelliJ as a build system.

![](assets/Pasted%20image%2020240624121904.png)

>Can this be changed later on.

#### Dependencies

> The below is probably true only when IntelliJ's builder is used. If Gradle, Maven are used the changes probably need to be made using build files.


A module can have dependencies, they are shown in 'Project Structure > Modules > Dependencies'. 

![](assets/Pasted%20image%2020240624125029.png)
It is of course also possible to add new dependencies, and they are of these types ([documentation link](https://www.jetbrains.com/help/idea/working-with-module-dependencies.html#add-a-new-dependency)) -

1. JAR or directories - Java archive or directory available locally.
2. Library - Select an existing library or create a new one as a dependency (where are they located though?)
3. Module Dependency - Another module in the project.

![](assets/Pasted%20image%2020240624125600.png)
#### Misc. errors

If there is an error that says 'Kotlin not configured', close the IDE, run the following command at project root.
```
rm -rf .idea .gradle gradle
```
Reopen the project, and let Gradle finish all its downloads
