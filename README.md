## SSCCE for [Gatling Community Support](https://groups.google.com/g/gatling/c/JUUghQqG_zk)

### Requirement
* Maven 3.5.x
* Java 8

### How To Run
* `mvn clean gatling:test -Dgatling.simulationClass=com.jak.sandbox.gatling.MySimulation -Denv.name=LOC`

### Expected
* When running simulation, `env.name` value should be substituted in `gatling.conf`. Below is the excerpt from [gatling.conf](src/test/resources/gatling.conf)
  ```hocon
  directory {
    data = src/test/resources/data/${env.name}               # Folder where user's data (e.g. files used by Feeders) is located
    #bodies = user-files/bodies           # Folder where bodies are located
    #simulations = user-files/simulations # Folder where the bundle's simulations are located
    #reportsOnly = ""                     # If set, name of report folder to look for in order to generate its report
    #binaries = ""                        # If set, name of the folder where compiles classes are located: Defaults to GATLING_HOME/target.
    #results = results                    # Name of the folder where all reports folder are located
  }
  ```

* In the console log you will see the substituted value. Log message will looks something like below
  ```
  15:25:03.324 [DEBUG] c.j.s.g.MySimulation - dir with substituted value = src/test/resources/data/LOC
  ```