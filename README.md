# vsoagent
Assorted Docker images with the new Build.vNext xplat agent baked in

## Currently Supported Tags
- `aspnet`: [vsoagent paired with Microsoft's ASP.NET vNext image](/aspnet/Dockerfile)
- `node`: [vsoagent paired with Docker's nodejs image](/nodejs/Dockerfile)
- `go`: [vsoagent paired with Docker's golang image](/go/Dockerfile)

## Usage
Feel free to clone this repo and use only the directory you wish for local image builds.  Replace the contents of the agent.config file with the parameters you need for setting up the agent.

Then, from a command prompt, type the following:
```
docker run -d <<image_name>> node host -u <<user>> -p <<password>>
```
