**My Docker & Monitoring Project**

This is my first DevOps project.
I built a web application that helps manage Docker containers, and I set up a whole system to monitor it and automate the deployment.

**What's inside?**

* **Web App:** A Python (Flask) app that shows your Docker images and lets you clean them up.
* **Monitoring:** I used **Prometheus** to collect data and **Grafana** to show it in nice graphs.
* **Automation:** I used **Jenkins** to build and run the app automatically.

**How the Jenkins Pipeline works**

I wrote a Jenkinsfile that does 3 things:
1. **Checkout:** Gets the latest code from GitHub.
2. **Build:** Creates a new Docker image of my app.
3. **Run:** Deletes the old container and starts a new one with the latest version.

How to run it

1. Make sure you have Docker and Docker Compose installed.
2. Clone this folder.
3. Run the command:
   bash
   docker-compose up -d --build
4. Access the tools:
    Web App: http://localhost:5000
    Monitoring: http://localhost:3000 (Grafana - Default login: admin/admin)
    
**Why I built this**

I wanted to learn how to bridgebetween development and operations. By connecting Docker, Jenkins, and Grafana, I learned how to create a persistent environment where an application can be built, deployed, and monitored automatically.

