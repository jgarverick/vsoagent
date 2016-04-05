# vsts-agent
Assorted Docker images with the new Build.vNext xplat agent baked in

## Currently Supported Tags
- `aspnet`: [vsoagent paired with Microsoft's ASP.NET vNext image](/aspnet/Dockerfile)
- `go`: [vsoagent paired with Docker's golang image](/go/Dockerfile)
- `java6`: [vsoagent paired with Docker's Java version 6 image](/java/java6/Dockerfile)
- `java7`: [vsoagent paired with Docker's Java version 7 image](/java/java7/Dockerfile)
- `java8`: [vsoagent paired with Docker's Java version 8 image](/java/java8/Dockerfile)
- `node`: [vsoagent paired with Docker's nodejs image](/nodejs/Dockerfile)
- `python`: [vsoagent paired with Docker's python image](/python/Dockerfile)
- `ruby`: [vsoagent paired with Docker's ruby image](/ruby/Dockerfile)


## Usage
Feel free to clone this repo and use only the directory you wish for local image builds.  Replace the contents of the agent.config file with the parameters you need for setting up the agent.

As of right now, you will need to configure the agent prior to first use.  Getting that automated is currently a WIP. 

Then, from a command prompt, type the following:
```
docker run -d <<image_name>> node host -u <<user>> -p <<password>>
```
