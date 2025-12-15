**Docker Scenario-Based Exercises**

**Question 1: Debugging a Docker Container Failure**

You’re a DevOps engineer deploying a Node.js application using Docker. You run docker run -d -p 3000:3000 my-node-app, but the container exits immediately. Using docker ps -a, you see the container status as Exited. How would you troubleshoot and resolve this issue?

Answer
To troubleshoot a container exiting immediately:

Check Logs: Run docker logs my-node-app to view error messages. Common issues include missing dependencies (e.g., npm install failed) or an incorrect command.
Inspect the Container: Use docker inspect my-node-app to check Config.Cmd or Config.Entrypoint. Ensure the command (e.g., node app.js) is valid.
Verify the Dockerfile: Check if CMD or ENTRYPOINT is correct, e.g., CMD ["node", "app.js"]. Update and rebuild if needed: docker build -t my-node-app ..
Test Interactively: Run docker run -it my-node-app sh to debug manually (e.g., node app.js).
Check Resources: Ensure the host has enough memory/CPU using docker stats.
Example Fix: If logs show node: command not found, update the Dockerfile to use FROM node:18, rebuild, and rerun.

Additional Notes
Always start with docker logs for error clues.
Use docker ps -a to check container status and ID.
Common issues include missing dependencies or crashing apps.
