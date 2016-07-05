1. Stagerunner is the object with nested functions that takes in an environment. On this environment we are able to run models through different stages, stop at certain stages, and replay the stages. 

2. Tundra container is an object that has a train and predict method. It takes a dataset and runs the model, trains the model, and saves this information needed to predict on new data. 

3. the config folder is used to set the global syberia configurations, configuration for testing / development / production, and routes configuration to controllers.

4. Resource is an embellished version of source, which takes a file's executables and brings them to the environment. We can then call the functions inside the resource like resource$function

5. Controllers are a type of abstraction that allow us to define how to compile / execute objects (like adapters or classifiers). Using controllers gives us access to the environment of the code to execute. We can set which files are executed under a type of controller by setting these in routes.

