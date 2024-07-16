# **Real-Time DevOps Monitoring Project Overview 🚀**
## **Introduction**
Welcome to our Real-Time DevOps Monitoring Project! 🌟 In this endeavor, we dive into the dynamic world of monitoring and alerting, ensuring the stability and performance of our infrastructure. Let’s explore the key components that power this project.

## **Key Components** 🛠️
1. **Prometheus Configuration**

   We’ve harnessed the power of Prometheus, an open-source monitoring toolkit. Here’s what we’ve set up:

   - Node Exporter: Collects essential system metrics from our virtual machines.
   - Blackbox Exporter: Probes endpoints (such as websites) to check availability.
   - Alert Manager: Orchestrates alerts and ensures timely notifications.

2. **Alert Rules** 🚨

   Our vigilant alert rules detect critical conditions:

   - Instance Downs: Immediate alerts when virtual machines go offline.
   - Website Down: Monitors website availability and notifies us promptly.
   - Host Out of Memory: Alerts us when memory resources are critically low.
   - High CPU Load: Ensures we’re aware of excessive CPU usage.

## **Implementation Scenarios** 📊
Let’s explore the scenarios we’re monitoring:

1. **Website Monitoring**:
   - Scenario: Our website goes down or becomes unavailable.
   - Alert Trigger: When the website status changes (e.g., HTTP requests fail).
   - Alert Action: We receive an immediate notification via email. 📧
   
2. **Local Machine Service Monitoring**:
   - Scenario: A service (e.g., Node Exporter) running on a Local machine fails.
   - Alert Trigger: Service status changes (process stops, port unresponsive).
   - Alert Action: Swift email notification to address the issue.🚨
## **How Alerts Work** 🚨
- **Detection**:
    - Prometheus continuously collects metrics from various sources (e.g., Node Exporter, Blackbox Exporter).
    - Alert rules define conditions (e.g., CPU load > 90%, website unreachable).
    - When conditions are met, alerts are triggered.
    
- **Alerting Workflow**:
    - Alert Manager receives alerts from Prometheus.
    - It groups related alerts (e.g., multiple VMs down) and deduplicates them.
    - Alert Manager routes alerts to configured receivers (e.g., email, webhook).
    - We receive timely notifications based on severity.
      
    <div align="center">
  <img alt="Real-Time-DevOps-Monitoring-Project" src="Images/Real-Time-DevOps-Monitoring-Projec.drawio.svg" ><br>
  <sup> Real-Time-DevOps-Monitoring-Project <sup>
  </div>
  
## **Prerequisites**
     1. 🤖 Ansible
     2. 🐧 Ubuntu on WSL (Windows Subsystem for Linux)
    
     
# **Project Setup** 🚀

1. **Clone the Git repository:**
   ```sh
   git clone https://github.com/badrivarun02/Real-Time-DevOps-Monitoring-Project.git
   ```
2. **Navigate to the Real-Time-DevOps-Monitoring-Project folder:**
   ```sh
   cd Real-Time-DevOps-Monitoring-Project
   ```  
3. **Install the Package using Ansible Playbook:**

   Ansible Command to install:
   ```sh
   ansible-playbook -i inventory.ini install_playbook.yml
   ```
   Inside the playbook, I've specified role names, so it installs packages like:

   - `prometheus_install`
   - `alertmanager_install`
   - `nodeExp_install`
   - `blackboxExp_install`
   - `maven_install`
   - `java_install`

4. **Launching the Applications:**
   After installing the packages, follow these steps to launch the applications:

   - **Prometheus:**
     Access Prometheus using the following URL: [http://localhost:9090](http://localhost:9090)

   - **NodeExporter:**
     Use this URL to access NodeExporter: [http://localhost:9100](http://localhost:9100)

   - **BlackBox Exporter:**
     Access BlackBox Exporter via: [http://localhost:9115](http://localhost:9115)

   - **Alertmanager:**
     Access Alertmanager at: [http://localhost:9093](http://localhost:9093)

---
# **Boardgame Project**🎲

## **Description**
The Boardgame project is a web application that allows users to clone a Git repository and build it using Maven. It provides a fun and interactive experience related to board games.

## **Prerequisites**
Before you get started, make sure you have the following installed:
- **Maven 3.9.6** or later
- **Java (openjdk-17-jre-headless)** or the latest version

## **Installation**
1. **Clone the Git repository:**

   ```bash
   git clone https://github.com/jaiswaladi246/Boardgame.git
   ```

2. **Navigate to the `Boardgame` folder:**
   ```sh
   cd Boardgame
   ```

3. **Build the project using Maven:**
   ```sh
   mvn package
   ```

4. **After building, you'll find the JAR file in the `target` folder. To run the project, use:**
   ```sh
   java -jar ./target/database_service_project-0.0.4.jar
   ```

5. **Accessing the Web Application:**

   - To access the web application, open a web browser and navigate to the following URL: [http://localhost:8080](http://localhost:8080).
   - The default port for the application is 8080.

## **Custom Port Configuration**

If you need to specify a specific port for your Java application, use the `--server.port` option followed by the desired port number. For example:

```bash
java -jar ./target/database_service_project-0.0.4.jar --server.port=8020
```
- Explore the board game features and enjoy!😊
   
---
# **Configuration Steps**

1. **Alert Rules Configuration:**
   - Add the [alert_rules.yml][another-file] to the Prometheus directory.
   
   [another-file]: roles/configcopy/files/alert_rules.yml
   - This file contains specific rules for alerting.

2. **Prometheus Configuration:**
   - Edit the Prometheus configuration file [prometheus.yml][another-file2]

   [another-file2]: roles/configcopy/files/prometheus.yml
     - Add the Alertmanager URL.
     - Include the rules file (`alert_rules.yml`).
     - Define job names (e.g., `NodeExporter`, `BlackBox Exporter`) under scrape configurations.
     - Ensure the website URL is configured for BlackBox Exporter.

4. **Alertmanager Configuration:**
   - In the [alertmanager.yml][another-file3], update the Gmail user ID and password according to your specific use case.

   [another-file3]: roles/configcopy/files/alertmanager.yml
     

### Deployment and Verification:

After editing these files, they should be copied to specific locations based on the instructions provided in the `tasks/main.yml` file under the `configcopy` role. By utilizing the `configcopy` role in your playbook, these changes will automatically propagate and trigger restarts of the relevant applications.

To apply the changes, run the following command:
```sh
ansible-playbook -i inventory.ini configfile_playbook.yml
```
Inside the playbook, I've specified role names, like:

   - `configcopy`
     
Finally, verify that the rules and targets are correctly added/configured in the Prometheus tool.

---
## **Setting Up App Passwords**🔐
 ### **Why App Passwords Matter**🤔

Before diving into the technical details, let's address the importance of app-specific passwords. If use 2-step verification for Google account, some mail clients may struggle to handle verification codes. App-specific passwords come to the rescue by allowing secure access to mail account without compromising security.

#### **Follow these steps to create an app-specific password for Google account:**

a. **Access Your Google Account:**
   - Navigate to your Google Account settings.
   - Click on "Security" in the left panel.

b. **App Passwords:**
   - Look for the "Signing in to Google" tab.
   - If you don't see the "App Passwords" option, consider the following:
     - Two-step verification might not be set up for your account.
     - Two-step verification could be configured for security keys only.
     - Your account might be associated with work, school, or another organization.
     - Advanced Protection could be enabled for your account.
   - If the option is not see, proceed to the next step.

c. **Creating an App-Specific Password:**
   - Search for "App Passwords" (you can use the search bar).
   - Sign in with your existing credentials.
   - On the "App Passwords" page, you'll find the option to create a new app-specific password.
   - Choose a descriptive name for your password (e.g., "Testing," "General Use").
   - Click "Create."
   - A unique app-specific password will be generated. Keep this secure; you won't need to remember it.

d. **Integration with AlertManager:**
   - In this project, store this app-specific password along with Gmail ID.
   - When configuring AlertManager, use this password to enable email notifications for alerts.

Remember that we will likely use this app-specific password only once during the initial setup. It ensures smooth communication between monitoring tools and Gmail account.

---

# **Testing the Project**

### Stopping Node Exporter

1. **Stop Node Exporter Service:**
   Execute the following command to stop the Node Exporter service:
   ```sh
   sudo systemctl stop node_exporter.service
   ```

### Terminating the Boardgame Website

2. **Terminate the Boardgame Website:**
   - Press Ctrl + C in the terminal where the Boardgame website is running.
   - This will stop the website.

### Checking Alerts

3. **Verify Alerts:**
   - Check alerts under the Prometheus tool.
   - Also, review alerts in Alertmanager.
   - Alertmanager will send notifications via Gmail, which we set up and configured in the alertmanager configuration file.
   - Verify that the email notifications are received in your Gmail inbox, indicating alerts:.
     - [FIRING:1] WebsiteDown (http://localhost:8080 blackbox critical)
     - [FIRING:1] InstanceDown (localhost:9100 node_exporter critical)
     - [FIRING:1] ServiceUnavailable (localhost:9100 node_exporter critical)

## Resolving Alerts

4. **Start NodeExporter and Boardgame Website Again:**
   - For Start NodeExporter:
     ``` sh
     sudo systemctl start node_exporter.service
     ```

     For Start Boardgame Website: 
     ```sh
     java -jar ./target/database_service_project-0.0.4.jar
     ```                                  
   - Check the status in Prometheus and Alertmanager.
   - Confirm that you receive notifications via Gmail, indicating resolved alerts:
     - [RESOLVED] InstanceDown (localhost:9100 node_exporter critical)
     - [RESOLVED] ServiceUnavailable (localhost:9100 node_exporter critical)
     - [RESOLVED] WebsiteDown (http://localhost:8080 blackbox critical)
       
# **Pro Tips: Configuration Validation for Prometheus, Node Exporter and AlertManager**🔍

1. **Prometheus Configuration:**

   First, make sure you have promtool installed (usually bundled with Prometheus).
Open a terminal window and navigate to the directory where your Prometheus configuration YAML file (prometheus.yml) is located.
Run the following command to check the configuration file:
   ```sh 
   promtool check config /etc/prometheus/prometheus.yml
   ```
   If the configuration is valid, you’ll receive a success message. Otherwise, it will highlight any issues.
   
2. **Node Exporter Configuration:**

   Similarly, ensure you have Node Exporter installed.
Navigate to the directory containing your Node Exporter configuration YAML file (node_exporter.yaml).
  
   Execute the following command to validate the configuration:
   ```sh 
   node_exporter --config.file /etc/node_exporter/node_exporter.yaml
   ```

   If everything is correct, Node Exporter will confirm successful loading. Otherwise, it will report errors.
   
3. **AlertManager Configuration:**

   For AlertManager, use the amtool utility.
Run the following command to validate your AlertManager configuration file (alertmanager.yml):
   ```sh 
   amtool check-config alertmanager.yml
   ```

   If the configuration is valid, you’re good to go. Otherwise, it will provide details on any issues.

# **Teardown**
1. Ansible Command to uninstall:
   ```sh
   ansible-playbook -i inventory.ini uninstall_playbook.yml
   ```    
    Inside the playbook, I've specified role names, so it uninstalls packages like:

   - `prometheus_uninstall`
   - `alertmanager_uninstall`
   - `nodeExp_uninstall`
   - `blackboxExp_uninstall`
   - `maven_uninstall`
   - `java_uninstall`

2. Terminate the Boardgame Website:
  - Press Ctrl + C in the terminal where the Boardgame website is running.
  - This will stop the website.
   

  #### NOTE:
   1. When uninstalling `Prometheus` and `Alertmanager` packages, there’s no need to mention the `configcopy` role explicitly. This role handles file copying, and any files it copied will automatically be removed during the uninstallation process. 
       
    
# **Learning Resources** 📚

I drew insights from the following blogs during my DevOps monitoring project:

1. [How to Install Prometheus and Grafana on Ubuntu - Linode Guide](https://www.linode.com/docs/guides/how-to-install-prometheus-and-grafana-on-ubuntu/)
2. [Installing Prometheus and Grafana on Ubuntu 22.04 LTS - Medium](https://ibrahims.medium.com/how-to-install-prometheus-and-grafana-on-ubuntu-22-04-lts-configure-grafana-dashboard-5d11e3cb3cfd)
3. [Installing Prometheus and Grafana on Ubuntu - Anton Putra](https://antonputra.com/monitoring/install-prometheus-and-grafana-on-ubuntu/#google_vignette)
4. [Prometheus Alert Manager Configuration - DevOpsCube](https://devopscube.com/prometheus-alert-manager/)
5. [How to Install and Configure Blackbox Exporter for Prometheus - DevConnected](https://devconnected.com/how-to-install-and-configure-blackbox-exporter-for-prometheus/)
6. [Prometheus and AlertManager Step-by-Step Configuration with Blackbox Exporter on Ubuntu 18.04 - Medium](https://rakeshjain-devops.medium.com/prometheus-and-alertmanager-step-by-step-configuration-with-blackbox-exporter-on-ubuntu-18-04-f2b76f52f1ad)
7. [Install Prometheus, Grafana, Node Exporter, and AlertManager - Medium](https://medium.com/@iqbal.hossain_5040/install-prometheus-grafana-nodeexporter-alertmanager-98496c29e495)

Additionally, I leveraged the power of Copilot AI and Gemini AI tools to fine-tune my automation scripts and troubleshoot errors. 🚀

# **Acknowledgments:** 🔗

Huge thanks to the DevOps community, the creators of the DevOps Shack series, and the supportive teams at Copilot AI and Gemini AI. Your contributions have been invaluable! 🙌
