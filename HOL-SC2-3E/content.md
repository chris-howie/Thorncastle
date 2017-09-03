
<!---
Version: 1.0 
-->
# Configure sanctioned application connectors
## INTRODUCTION MESSAGE
<Author: please provide.>
## COMPLETION MESSAGE
In this exercise, you .... In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Sign in to Office 365
**\(1\)** Sign in to Office 365 portal (https://portal.microsoftonline.com).

### Start your free trial
**\(1\)** From the Admin center, click on **subscriptions** under **Billing**, and choose **Add Subscription**. **\(2\)** Scroll down until you find Microsoft Cloud App Security and choose **Start Free trial**. **\(3\)** Confirm your order by clicking **Try now**.

### Locate your user account
**\(1\)** Go to the Office365 admin portal, and under **Users**, choose **Active Users** and find your user account.

### Assign a license to your user account
**\(1\)** Assign a Microsoft Cloud App Security license to your user account.

### Create a tenant
**\(1\)** Create a new Box tenant from the following link: https://app.box.com/signup/n/developer. **\(2\)** Sign in to the box portal from https://account.box.com/login and upload all files to the Box tenant from the Lab_files\upload_to_Box folder on the desktop on CAS Utility VM.

### Share a file
**\(1\)** Publicly share one of the file Workplace Innovation using a public link. **\(2\)** Share another file with your personal email address.

### Browse to the Cloud App Security portal
**\(1\)** Browse to Cloud App Security portal (https://portal.cloudappsecurity.com). **\(2\)** Navigate to Investigate > Connected Apps.

### Connect a box
**\(1\)** On the **Connected Apps** page, click the plus sign (+), and select **Box**. **\(2\)** Click **Connect Box**, and then **follow this link**. **\(3\)** Enter credentials created in step 1, and click **Grant access to Box**.

### Validate deployment
**\(1\)** Click close to navigate back to connected apps page. **\(2\)** Refresh the page to validate deployment.

#### :bulb: KNOWLEDGE
Cloud App Security uses APIs provided by cloud provider. Some operations such as scanning all files in the tenant require many API calls and therefore are spread over time. Scan time may vary depending on the size of tenant, number of users and number of files that need to be scanned.



# Create a snapshot report
## INTRODUCTION MESSAGE
<Author: please provide.>
## COMPLETION MESSAGE
In this exercise, you .... In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Create a snapshot report
**\(1\)** Navigate to Gear > Cloud Discovery Settings > Manage Snapshot Reports, and then click **Create Snapshot Report**.

#### :bulb: KNOWLEDGE
Snapshot Reports are the manual method of uploading files into Cloud App Security. You can upload batches of 20 logs at a time and they will parse into their own separate report. Any discovery policies you create will not apply to these types of reports.

### Name your snapshot report
**\(1\)** In the new screen, provide a name for your report, such as _Cisco_Sample_Report,_ and select **Cisco IronPort WSA** from the **Data Source** dropdown.

#### :bulb: KNOWLEDGE
A Data Source is a representation of a single device to Cloud App Security. For snapshot reports, the data source determines the expected log format to ensure successful parsing of data.

### Download a sample snapshot report
**\(1\)** In the yellow popup, click **View and Verify**. This will show you the expected format for the Cisco IronPort WSA log. **\(2\)** Click **Download Sample** to download a zip file that contains an up-to-date sample log file. **\(3\)** Click **close** on the pop-up window, but do not leave the screen.

#### :bulb: KNOWLEDGE
These sample log files are useful for POC’s or demo’s where you want to show a customer the process for either manually or automatically uploading logs into MCAS.

### Parse the log
**\(1\)** Under **Choose traffic logs**, click **Browse**. **\(2\)** Select the Cisco IronPort WSA sample .zip file that you just downloaded, and then click **Open**.**\(5\)** **\(3\)** Click **Create** to begin the parsing process for the log.

#### :bulb: KNOWLEDGE
You can upload single logs or zipped files as we did here, this is useful in case you want to compress larger logs from customers.

### View the pending log
**\(1\)** The snapshot report will now show as pending.

#### :bulb: KNOWLEDGE
We manually uploaded a sample log in this module which is a great way to quickly show customers data in the Discovery dashboard, test to make sure logs will successfully parse before configuring automatic upload, and put some sample data in your own demo tenant.



# Configure a log collector
## INTRODUCTION MESSAGE
<Author: please provide.>
## COMPLETION MESSAGE
In this exercise, you .... In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Connect to the Log Collector
**\(1\)** Open PuTTy from the CASUtility VM, and connect to the specified Log Collector IP address that was provided to you for your demo environment.

#### :bulb: KNOWLEDGE
In the below screenshots, we are connecting to 192.168.0.106 on port 22, your IP address will be different. The Log Collector is running on Hyper-V and is an Ubuntu Server image that is setup to run the necessary services receive and send log files to MCAS. The Log Collector at this point is not configured to connect to your tenant, which is what we will do next.

### Sign in to the support account
**\(1\)** Sign in with the **Username:** support and the **Password:** adallom200.

#### :bulb: KNOWLEDGE
The ‘support’ account is a special account that has root privileges to the VM. In a normal deployment, you would be prompted to change the default password on your first login.

### Change the IP configuration
**\(1\)** Run the command `sudo network_config`. **\(2\)** Answer Y to "Would you like to change the current IP configuration?." **\(3\)** For the remainder of the questions, answer N.

#### :bulb: KNOWLEDGE
The purpose of this small exercise is to show you what options are available to you when configuring the networking for the VM. For this lab you _should not_ be changing any of the network parameters.

### Add a data source
**\(1\)** Leave PuTTy running in the background, and go back to the MCAS console in the browser. **\(2\)** Navigate to Gear > Log Collectors. **\(3\)** Click **Add Data Source**.

#### :bulb: KNOWLEDGE
We are creating a data source which will represent a fictitious Cisco device. This data source will dictate where our sample log will be uploaded and how it will be parsed. Reminder, when working with customer environments, you need to create a unique data source for each device the customer plans to have logs sent to the collector.

### Complete the Add data source dialog box
**\(1\)** Fill out the form in the pop-up window. **\(2\)** For **Name**, enter **Cisco_IronPort_001**. **\(3\)** For **Data Source**, select **Cisco IronPort WSA**. **\(4\)** For **Receiver Type**, select **FTP**. Click **Add**.

#### :bulb: KNOWLEDGE
By specifying the receiver type as FTP, when we bootstrap the log collector in future steps, this will create a folder for the data source underneath a FTP folder where it will expect full logs to be sent. Had we selected ‘Syslog’, the folder would be created under the syslog folder and a syslog listener service would be running on the VM to receive the syslog data stream, and it would dump those entries to a flat file in that folder, where it would be uploaded automatically to MCAS.

### Add a log collector
**\(1\)** Click the **Log Collectors** tab. **\(2\)** Select **Add Log Collector**.

#### :bulb: KNOWLEDGE
Even though the Log Collector VM has technically been deployed, it has not yet been configured to connect to your tenant. In the next step we are letting MCAS know that a collector has been deployed and it will be associated with the Cisco IronPort WSA data source that will receive logs over FTP.

### Associate a data source with your log collector
**\(1\)** In the pop-up window, in **Name**, enter **LogCollector_001**. **\(2\)** In **Data Sources**, select the box, and choose the data source that you just created. **\(3\)** Click **update**. You will be provided a token that you should now copy to your clipboard.

#### :bulb: KNOWLEDGE
In this lab we are associating one data source to one log collector, however, you can have multiple data sources per log collector in a customer environment. The log collector can handle ~50GB/hr of logs, so having multiple low-volume data sources in a single collector is an approved deployment model. Note, you cannot have a single data source associated to two different Log Collectors; if you try, the console will throw an error.

### Connect your collector to your tenant
**\(1\)** Go back to your PuTTy session, and run the following command:

#### :calling: COMMAND
sudo collector_config <paste your token>

**\(2\)** Right-click in the terminal to paste in your token. **\(3\)** You are prompted to enter your domain information. **\(4\)** Go back to the console, and in the URL bar, copy the following to your clipboard (do not copy `https://`):

#### :calling: COMMAND
<yourtenant>.portal.cloudappsecurity.com

**\(5\)** Paste or type that info into your PuTTy session and press Enter.

#### :bulb: KNOWLEDGE
The collector_config command takes the token, checks in with the MCAS service and connects your collector to your tenant using the API token. This is how the collector knows what logs it will receive and where they will be sent.

### Establish an FTP connection to the collector
**\(1\)** Open WinSCP from the Desktop, and provide your Log Collector IP address. **\(2\)** Ensure that the Port Number is set to **21**. **\(3\)** In **Username**, enter **discovery**. **\(4\)** In **password**, enter **12345678**. **\(5\)** Click **Login**. This should open a FTP connection to the collector.

#### :bulb: KNOWLEDGE
The ‘discovery’ account permissions are different from ‘support’. This account does not have root access. The credentials we used here are the default FTP credentials used by all Log Collectors, and unlike the ‘support’ account, you will not be prompted to change this password on your first login.

### Access the JSON configuration file
**\(1\)** WinSCP should login, and you should see a folder in the right pane that is named the same as your Data Source (likely _Cisco_IronPort_001)_. **\(2\)** Double-click the folder to go inside, and all you should see is a .json configuration file.

### Copy the JSON file to your data source folder
**\(1\)** Extract the sample zip file you downloaded in the snapshot report module. **\(2\)** Drag the .log file into the right pane of WinSCP to copy it into the Data Source folder. **\(3\)** Click the little green ‘refresh’ button on the right side. **\(4\)** Notice that the log file disappears.

#### :bulb: KNOWLEDGE
We just simulated a log file being sent over FTP to the collector’s data source folder. Normally you would configure a device to send the logs over FTP automatically, but we simply dragged and dropped the file into the folder ourselves. This is a great way to showcase the way the collector works as part of a customer demo. The log file disappeared when we refreshed the pane, because the file has been uploaded and moved out of the folder to a temporary backup folder. This backup folder will hold the latest log that was uploaded, and be overwritten by newer logs as they come in.

### View the status of your log file
**\(1\)** In the MCAS console in your browser, navigate to Gear > Governance Log. **\(2\)** You should now see your recent log file showing as _pending_.

#### :bulb: KNOWLEDGE
Unlike snapshot reports where we manually upload a batch of logs in the console, this was a simulated automated upload scenario. Logs uploaded in this way are aggregated into what the console calls a ‘Global Stream’. All data sources will have their data parsed and added to this Global view so you can see all your parsed data at once across all devices. When creating discovery policies, it’s important to remember that policies only apply to parsed data that makes it’s way to the Global Stream, not snapshot reports. If you intend to work with customers to test discovery policies, you will want to make them first, then configure a log collector to upload the logs.



# Troubleshoot the log collector
## INTRODUCTION MESSAGE
<Author: please provide.>
## COMPLETION MESSAGE
In this exercise, you .... In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Connect to your log collector
**\(1\)** Open PuTTY, and connect to your Log Collector’s IP on port 22. **\(2\)** If you haven’t already, sign in: In **Username:**, type **support**, and in **Password:**, type **adallom200**. **\(3\)** Right-click the top window bar and select **Event Log**. **\(4\)** Review the events, and then close the window.

#### :bulb: KNOWLEDGE
PuTTY is a useful tool for remote administration of machines over SSH, and it allows administrators to log their session. The PuTTY event log is a useful tool for capturing the full remote session and sending it to support.

### Review the list of folders
**\(1\)** Type `cd /var/`. **\(2\)** Type `ll`. **\(3\)** Review the list of folders, and note the adallom and log folders.

#### :bulb: KNOWLEDGE
There are two primary areas where you will look for information when investigating the Log Collector. The /var/adallom folder is where you will investigate issues with the syslog or ftp logs being sent to the collector. The /var/log folder is where you will investigate issues with the collector itself.

### View the discoverylogsbackup, ftp, and syslog folders
**\(1\)** Type `cd adallom`. **\(2\)** Type `ll`. **\(3\)** Note the discoverylogsbackup, ftp, and syslog folders. **\(4\)** Change directory into each of the folders and explore what’s inside. **\(5\)** Once you are done exploring the folders, type `cd /var` and read the learning notes for this step.

#### :bulb: KNOWLEDGE
The discoverylogsbackup folder contains the last file that was sent to MCAS. This is useful for looking at the raw log in case there are parsing issues. If you setup the collector to receive syslog messages, the syslog folder is where the flat file of aggregated messages will reside until it is uploaded. This happens every 20 minutes. Finally, the var/adallom/ftp/discovery/ folder contains the data source folders where you would send log files for automated upload. This is also the default folder when logging into the collector with FTP credentials. (Fun fact: Adallom was the company Microsoft acquired which became Cloud App Security.)

### View the columbus and columbusinstaller folders
**\(1\)** Type `cd /var/log/adallom`. **\(2\)** Type `ll`. **\(3\)** Explore the columbus and columbusInstaller folders.

#### :bulb: KNOWLEDGE
The columbus folder is where you will find log files useful for troubleshooting issues with the collector sending files. In the log-archive folder you can copy previous logs compressed as .tar.gz files off the collector to send to support. The columbusInstaller folder is where you will find logs pertaining to the configuration and bootstrapping of the collector. For example, trace.log will show you the bootstrapping process for when you ran `sudo collector_config <token>`. If there were an error when you ran this command, you could see where the issue was by reviewing this log. **Note:** Columbus is a legacy code name for the Log Collector from before Adallom was acquired.



# Create a discovery policy
## INTRODUCTION MESSAGE
<Author: please provide.>
## COMPLETION MESSAGE
In this exercise, you .... In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Create a new app discovery policy
**\(1\)** In the Cloud App Security portal, select **Control > Policies**. **\(2\)** Select **Create Policy > App Discovery Policy**.

#### :bulb: KNOWLEDGE
This module only covers creating an App Discovery Policy, but do know there is also a Cloud Discovery anomaly detection policy that looks for deviation from normal behavior based on uploaded logs. If you have time, you are encouraged to explore this policy as well.

### Apply a template to the policy
**\(1\)** In the **Policy Template** list, select **New risky app**. **\(2\)** In the dialog box that appears, select **Apply Template**.

#### :bulb: KNOWLEDGE
These policy templates exist to help customers quickly start realizing value from Discovery. Each of the templates pre-configures a number of policy settings and the customer can then start to customize specific parameters for their needs.

### Customize the policy
**\(1\)** Change the Policy name, description, severity, filters, and frequency to look like the example. **\(2\)** Select **Create**. You have just created an App Discovery Policy. **\(3\)** Optionally, set the governance option on the policy to tag the app as unsanctioned.
<!--- TIM: Step 1 relies completely on the associated graphic for the settings. We'll need to reword this procedure to eliminate that reliance. --->
#### :bulb: KNOWLEDGE
Discovery policies will only trigger based on new incoming log data, not old data. This is why you should set your discovery policies as soon as possible. Select **Edit and Preview Results** in the upper right of filters box. This will show you what apps will be triggered based on your set metadata filters. This is a useful feature as well in Activity and File policies.



# Configure the activity policy
## INTRODUCTION MESSAGE
In this exercise, you configure an activity policy to detect multiple failed user sign-in attempts from a risky IP address.
## COMPLETION MESSAGE
In this exercise, you configured an activity policy to detect multiple failed user sign-in attempts from a risky IP address. In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Identify the IP address of your activity log
**\(1\)** Go to to Investigate > Activity Log, and identify your IP address by filtering **App** on Microsoft Cloud App Security and **Activity type** as log on and copy it. **\(2\)** Select **Settings > IP Address Ranges**, then select **Add IP address range**.

### Assign a risk category
**\(1\)** Assign the Risky category to the logon IP by populating the **IP address ranges& Category** fields as shown below.
<!--- TIM: Step 1 relies completely on the associated graphic for the settings. We'll need to reword this procedure to eliminate that reliance. --->

### Select a policy
**\(1\)** Navigate to **Control**, and then select **Policies**. **\(2\)** Select **Create policy > Activity Policy**.

### Apply a template
**\(1\)** Choose the **Multiple failed user logon attempts to an app** template, and then select **Apply Template**. **\(2\)** Change the **minimum repeated activities** parameter to **2** so that the policy will trigger after two failed logon attempts.

### Add a category filter
**\(1\)** Add an IP category filter on Risky IP addresses.

### Configure the actions to be taken when the policy is triggered
**\(1\)** Set the policy to send an alert only. Optionally you can choose to send a text message alert or even suspend the user account. **\(2\)** Save the policy.

### Test the policy
**\(1\)** Test the policy by navigating to box portal and initiating three failed logon attempts. **\(2\)** Navigate to the alerts page to review alerts generated from this policy.

#### :bulb: KNOWLEDGE
There may be a slight delay to populate the events in the console.



# Configure the file policy
## INTRODUCTION MESSAGE
In this exercise, you configure a file policy to detect multiple sensitive files that have been shared with personal domains and remove external collaborators.
## COMPLETION MESSAGE
In this exercise, you configured a file policy to detect multiple sensitive files that have been shared with personal domains and remove external collaborators. In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Locate your file policy
**\(1\)** Select **Control > Policies**. **\(2\)** Select **Create policy > File Policy**.

### Apply a template
**\(1\)** Choose the **File shared with personal email addresses** template, and then select **Apply template**.

### Configure the policy
**\(1\)** Select the **Enable** beside **Content inspection. **\(2\)** From **Include files that match a preset expression**, select **US: PII: Social Security number**. **\(3\)** Under **governance**, select **remove External Users**. **\(4\)** Save the policy.

### View matched events
**\(1\)** Navigate to the **policies** page, and select the policy name to see matched events.

#### :bulb: KNOWLEDGE
In this policy, we are using the built in DLP engine to detect PII content. We can also connect to on-premises DLP systems over ICAP to extend same policies to Cloud Applications.



# Configure the SIEM agent
## INTRODUCTION MESSAGE
In this exercise, you set up the SIEM agent to send activities and alerts from Cloud app security to Kiwi Syslog server. Cloud app Security SIEM agent runs on a server in customer’s network and pulls alerts and activities from the service and streams them into SIEM server. It pulls the activities and alerts using Cloud App Security RESTful APIs. The traffic is then sent over an encrypted HTTPS channel on port 443.
## COMPLETION MESSAGE
In this exercise, you set up the SIEM agent to send activities and alerts from Cloud app security to Kiwi Syslog server. In the next exercise, you will ....
<!--- AUTHOR: Please provide INTRODUCTION MESSAGE and COMPLETION MESSAGE text. --->
### Locate the SIEM agent
**\(1\)** Go to **Settings > Security Extensions > SIEM Agent**.

### Name your agent
**\(1\)** Click **Start wizard**, and enter a name of your choice in **Add agent name**. **\(2\)** Select **Generic CEF** for **Select your SIEM format**, and then select **Next**.

### Configure ports
**\(1\)** Populate **Remote syslog host**, **remote syslog port**, and select **UDP** for **protocol** as shown below. **\(2\)** Select **Next**.
<!--- TIM: Step 1 relies completely on the associated graphic for the settings. We'll need to reword this procedure to eliminate that reliance. --->

### Enable the activities switch
**\(1\)** By default, only alerts are sent to SIEM. Enable the activities switch, as well. **\(2\)** You may also granularly select activities and alerts based on various filters. For the lab leave the selection as all activities.
<!--- TIM: Step 1 relies completely on the associated graphic for the settings. We'll need to reword this procedure to eliminate that reliance. --->

### Replace the token
**\(1\)** Copy the token generated, and navigate to desktop\lab_files\SIEM agent\command.txt. **\(2\)** Replace the word _TOKEN_ in the following command with the generated token.

#### :calling: COMMAND
```java -jar mcas-siemagent-0.93.64-signed.jar [--proxy 127.0.0.1[:514]] --token TOKEN```

### Verify that activity alerts appear
**\(1\)** Open the SIEM_install_prompt in the same folder and paste the above command. **\(2\)** Validate that activities and alerts are now shown in Kiwi syslog server.

#### :bulb: KNOWLEDGE
When SIEM is first integrated with Cloud App Security, activities and alerts from the last two days will be forwarded to the SIEM.
