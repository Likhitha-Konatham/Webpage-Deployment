# Jenkins-Pipeline
# Start the thing
Project: Jenkins Automated Static Website Deployment

1. Create Jenkins Pipeline:
   - **Objective**: Automate the deployment process.
   - **Action**: Write a `Jenkinsfile` with three stages:
     - **Checkout**: Clone the repository from GitHub.
     - **Build**: (Optional) Process or build files if needed.
     - **Deploy**: Copy `index.html` to the web server’s directory.

**2. Set Up Webhooks:**
   - **Objective**: Automatically trigger Jenkins builds on code changes.
   - **Action**: Configure a GitHub webhook to notify Jenkins when changes are pushed to the repository, initiating a build process.

**3. Grant Jenkins Access:**
   - **Objective**: Allow Jenkins to write files to the web server directory.
   - **Action**: Change the ownership of `/var/www/html` to the Jenkins user:
     ```bash
     sudo chown -R jenkins:jenkins /var/www/html
     ```

**4. Run Pipeline:**
   - **Objective**: Execute the deployment process.
   - **Action**: Trigger the Jenkins pipeline to run the stages defined in the `Jenkinsfile`, which will deploy `index.html` to `/var/www/html`.

**5. Verify:**
   - **Objective**: Ensure successful deployment.
   - **Action**: Open a browser and navigate to `http://<server-ip>/index.html` to check if the `index.html` page is displayed correctly.
