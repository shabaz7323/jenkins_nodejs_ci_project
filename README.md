Jenkins Docker CI/CD project

Files included:
- app.js
- package.json
- Dockerfile
- .dockerignore
- Jenkinsfile (Docker CI/CD)
- README.md

Next steps:
1) Install Docker on your Jenkins host (Windows). Ensure the 'docker' command works for the Jenkins service user.
2) Create Docker Hub credentials in Jenkins:
   - Manage Jenkins -> Credentials -> System -> Global -> Add Credentials
   - Kind: Username with password
   - Username: shabaz7323
   - Password: <your Docker Hub password or access token>
   - ID: docker-hub-credentials
3) Make sure Jenkins node can run 'docker build' and 'docker push' manually before running the job.
4) Create/Update your Pipeline job (Pipeline script from SCM) pointing to this repo's Jenkinsfile and run it.
