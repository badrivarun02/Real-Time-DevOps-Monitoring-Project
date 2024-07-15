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
  <img alt="Real-Time-DevOps-Monitoring-Project" src="Images/Real-Time-DevOps-Monitoring-Projec.drawio.svg" width="400" height="100"><br>
  <sup>Sample display of image in HTML format <sup>
  </div>
  ![](Images/Real-Time-DevOps-Monitoring-Projec.drawio.svg)
  
## **Prerequisites**
     1. 🤖 Ansible
     2. 🐧 Ubuntu on WSL (Windows Subsystem for Linux)
    
     
# **Project Setup** 🚀

1. Clone the Git repository:
   ```sh
   git clone https://github.com/badrivarun02/Real-Time-DevOps-Monitoring-Project.git
   ```
2. Navigate to the Real-Time-DevOps-Monitoring-Project folder:
   ```sh
   cd Real-Time-DevOps-Monitoring-Project
   ```  
3. Install the Package using Ansible Playbook:

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
   - `configcopy`

   NOTE:
   1. Within the `configcopy` role, you’ll find directories and navigate `files` folder containing essential configurations such as `alert_rules.yml`, `alertmanager.yml`, and `prometheus.yml`. These files are designed to be copied to specific locations based on the instructions provided in the `tasks/main.yml` file.
  
   2. In the `alertmanager.yml` file, make sure to edit the Gmail user ID and password according to your specific use case.If any other changes are necessary in the remaining configuration files, update them accordingly. By utilizing the `configcopy` role in your playbook, these changes will automatically propagate and trigger restarts of the relevant applications.

## **Why App Passwords Matter**

Before diving into the technical details, let's address the importance of app-specific passwords. If use 2-step verification for Google account, some mail clients may struggle to handle verification codes. App-specific passwords come to the rescue by allowing secure access to mail account without compromising security.

## **Setting Up App Passwords**🔐

Follow these steps to create an app-specific password for Google account:

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

4. Ansible Command to uninstall:
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
   

      NOTE:
   1. When uninstalling `Prometheus` and `Alertmanager` packages, there’s no need to mention the `configcopy` role explicitly. This role handles file copying, and any files it copied will automatically be removed during the uninstallation process. 
       
     


# **Boardgame Project**🎲

## **Description**
The Boardgame project is a web application that allows users to clone a Git repository and build it using Maven. It provides a fun and interactive experience related to board games.

## **Prerequisites**
Before you get started, make sure you have the following installed:
- **Maven 3.9.6** or later
- **Java (openjdk-17-jre-headless)** or the latest version

## **Installation**
1. Clone the Git repository:

   ```bash
   git clone https://github.com/jaiswaladi246/Boardgame.git
   ```

2. Navigate to the `Boardgame` folder:
   ```sh
   cd Boardgame
   ```

3. Build the project using Maven:
   ```sh
   mvn package
   ```

4. After building, you'll find the JAR file in the `target` folder. To run the project, use:
   ```sh
   java -jar ./target/database_service_project-0.0.4.jar
   ```

## Usage
- Access the web application by opening a browser and navigating to the appropriate URL.
- Explore the board game features and enjoy!

# **Testing the Project**

1. **Stop Node Exporter:**
  
   Execute the following command to stop the Node Exporter service:
     ```sh
     sudo systemctl stop node_exporter.service
     ```

2. **Terminate the Boardgame Website:**

   Press Ctrl + C in the terminal where the Boardgame website is running.
After stopping the website, check the alerts in Prometheus.

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




