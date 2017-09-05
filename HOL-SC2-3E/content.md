
<!---
Version: 1.0 
-->
# Cloud App Security
## INTRODUCTION MESSAGE
Microsoft Cloud App Security is a service that provides you with deep visibility into the software-as-a-service (SaaS) apps in use at your organization. The main benefits Cloud App Security are:

* Discovery of all SaaS apps in operation by your users (Risk assessment)
* Control over which SaaS apps are allowed to run, eliminating the "shadow IT" problem (Policy-based enforcement)
* Protection of your users and data by constraining data flows out of your organization (Data Loss Protection and Data Sharing Control)

> **Note**: Shadow IT is a security issue that occurs when users install IT solutions without explicit organizational approval.

In this lab, you will familiarize yourself with Microsoft Cloud App Security. By its conclusion, you will know how to:

* Activate a Cloud App Security subscription
* Perform cloud discovery of SaaS apps in use
* Build app connections with popular SaaS platforms
* Mark SaaS apps as either sanctioned or non-sanctioned
* Define policies to control SaaS app behavior

## COMPLETION MESSAGE
Congratulations on completing this lab! You should have a much clearer idea in the ways Microsoft Cloud App Security helps to secure your organization's app environment. Specifically, you know how to perform cloud app discovery, sanction and unsanction SaaS apps, configure app integrations, and define and monitor cloud app policies.
### Sign in to Office 365

<!--- How are learners authenticating here? Not with their own accounts, I hope... --->

Because Cloud App Security is a component of the Office 365 product suite, you first need to authenticate to Office 365.

1. Sign in to Office 365 portal (https://portal.office.com).
2. In the Office 365 Start Screen, click **Admin**. The Office Admin Center appears.

### Start your Cloud App Security free trial

Cloud App Security is available as an Office 365 add-on product ($5 per user per month as of this writing) or as a component of the Enterprise Mobility + Security E5 stock-keeping unit (SKU). In this lab, you will register for the 30-day free trial.

1. In the Office Admin Center navigation bar, click **Billing > Subscriptions**.
2. In the **Home > Subscriptions** page, click **Add subscription**.
3. Scroll down until you find Microsoft Cloud App Security and choose **Start Free trial**.
4. Confirm your order by clicking **Try now**.

> **Note**: A link to the Cloud App Security dashboard appears in the Office Admin Center under **Admin centers > Cloud App Security**.

### Assign a Cloud App Security license to your user account

You will be unable to configure Cloud App Security until you assign a license to your Office 365 user account.

1. In the Office Admin Center navigation bar, click **Users > Active Users**. 
2. In the **Active Users** list, click your user account.
3. In your user Properties page, find **Product licenses** and then click **Edit**.
4. In the **Product licenses** page, turn on the **Microsoft Cloud App Security** license, and then click **Save**.
5. In your user Properties page, click **Close**.

### Set up Cloud Discovery

The best way to give Microsoft Cloud App Security a head start on understanding the SaaS apps in use at your organization is to upload a log file from your corporate firewall. Cloud App Security hosts a database containing over 15,000 SaaS apps. Therefore, its likely that Cloud App Security can report on most, if not all, your SaaS traffic.

1. In the Office Admin Center navigation bar, click **Admin centers > Cloud App Security**.

> **Note**: You can also browse directly to the Cloud App Security dashboard via the URL https://portal.cloudappsecurity.com.

2. In the Cloud App Security dashboard top navigation bar, click **Discover > Create snapshot report**.
3. In the **Create new Cloud Discovery snapshot report** page, fill out the form using the following values:

* Report name: **Sample Discovery Report**
* Description: **Testing - not for production use**
* Data source: **Cisco ASA Firewall**
* Anonymize private information: *unselected*

4. In the **Verify your log format** section, click **View and verify**. It's important to ensure the firewall log you submit to Cloud App Security is formatted correctly so Cloud App Security can parse it fully. In this exercise, we will use a sample log provided by Microsoft.
5. In the **Verify your log format** window, click **Download sample log**. 
6. Open File Explorer from the Windows Taskbar, browse to the **Downloads** folder, and extract the Cisco ASA firewall sample logs by right-clicking the .zip archive, selecting **Extract all** from the shortcut menu, and then clicking **Extract** in the **Extract Compressed (Zipped) Folders** dialog box.
7. In the **Verify your log format** window, click **Close**.
8. In the **Create new Cloud Discovery snapshot report** page, under **Choose traffic logs**, click **Browse**.
9. in the **Open** dialog box, browse to **Downloads > cisco-asa-firewall-demo_log.log** and select **cisco-asa-firewall-1_demo-log.log**, and then click **Open**.
10. Click **Create** to start the cloud discovery process. you are taken to the **Cloud Discovery settings . Manage snapshot reports** page.

> **Note**: It would take approximately five minutes for Cloud App Security to parse the sample log. You may need to press **F5** to refresh your browser.

### Inspect a Cloud Discovery report

Once the newly created snapshot report shows in **Ready** status, you are ready to inspect the report.

1. In the **Manage snapshot reports** page, find **Sample Discovery Report** and click **Ready**. The Cloud Discovery dashboard appears.

The Cloud Discovery report lists detected SaaS apps, associated IP addresses, and potentially user accounts. Each detected app is analyzed by Cloud App Security to assess its security risk. 

2. In the Cloud Discovery dashboard, click the **Discovered apps** tab.

You now have full visibility as to which SaaS apps are in operation in your corporate network. You can choose to sanction any apps that you want to allow and manage; unsanctioned apps are SaaS apps that you explicitly want to block.

3. Scroll down the list to find the **Concur** entry, open its context menu, and select **Sanctioned**.
4. Find the **Box** entry, open its context menu, and select **Unsanctioned**.

> **Note**: Sanctioned apps display with a green check icon. Unsanctioned apps display with a red forbidden icon.

5. In the Cloud Discovery dashboard, click the **IP addresses** tab.
6. In the **Top 100 IP addresses** list, click the **Traffic** column to perform an inverse sort.

The IP addresses tab notifies you of the "chattiest" IP addresses, which may be associated with particular organizational users and potential "shadow IT" SaaS apps.

7. In the Cloud Discovery dashboard, click the **Users** tab. No users are contained in the firewall log. We need to create an app connection in order to get user-level details.

> **Note**: It is out of scope for this lab, but you can configure Cloud App Security to run Cloud Discovery jobs automatically on a schedule.

### Sanction apps manually

There may be occasions where, for whatever reason, your firewall logs are not sufficient to detect known SaaS app activity. In this case, you can sanction or unsanction apps manually by querying the Microsoft Cloud App Catalog.

1. In the Cloud App Security dashboard top navigation bar, click **Discover > Cloud app catalog**.
2. In the **Browse by category** list, click **Productivity**.

Notice that each app is assigned a numeric score (with 10 being the highest) as to its overall risk profile.

3. In the apps list, click **Google Keep**. Scan the Cloud App Security profile metadata, which is organized into the following sections:

* **General**: Domain information, privacy policy, consumer popularity
* **Security**: Auditing, encryption, whether the application is routinely subjected to penetration tests
* **Compliance**: The industry or regulatory compliance certifications possessed by the app vendor

4. In the **Actions** column, click to mark the app as **Sanctioned**.
5. From the Cloud App Security top navigation bar, click **Discover > Discovered Apps**.
6. Navigate to the **Discovered Apps** tab.
7. In the filter bar under **App Tag**, click **Sanctioned**. This filters the view to display only apps you have sanctioned for your organization. You can do the same thing for unsanctioned apps.

### Connect apps

Cloud App Security has deep application programming interface (API) access to many leading SaaS platforms, including:

* Office 365
* Okta
* Google G Suite
* Salesforce
* Dropbox
* Amazon Web Services (AWS)
* Box
* ServiceNow

The chief advantage to creating an app connection is much deeper control over the data flow. For instance, if your users have Office 365 accounts, then it makes sense to enable the Office 365 app connector so you can perform user-level security and administration tasks.

In this procedure we will inspect Cloud App Security app connectors.

1. Click **Cloud App Security** in the upper-left corner to return to the Cloud App Security dashboard. 
2. From the top navigation bar, click **Investigate > Connected Apps**.
3. In the app list, click **Office 365**. The **Office 365 Collaboration** page appears. On this page you can explore the API connection points between the connected app and Microsoft Cloud App Security. The user interface is divided into six tabs:

* **Dashboard**: Active users plotted on a world map
* **Info**: General, security, and compliance metadata and Cloud App Security threat assessment
* **Accounts**: User accounts linked to the SaaS app
* **App permissions**: OAuth permissions granted to the app
* **Live activity**: Active connections to the app platform
* **Alerts**: Security alerts raised by Cloud App Security

4. In the **Office 365 Collaboration** page, click the **Accounts** tab.
5. In your account entry, open the menu in the last column. Notice that you can report on the user's activity within Office 365, and you can perform administrative actions such as requiring that the user reauthenticate or even suspend the user.
6. Click **Investigate > Connected Apps** to return to the **Connected apps** list.
7. Open the New Connection menu and select **G Suite**.
8. In the **G Suite** dialog box, click **Connect G Suite**. In order to connect an app to Cloud App Security, you need to authenticate to the remote service with an administrator account. Depending on the app service, you may need additional information. For example, G Suite requires an App ID and digital certificate. In this lab we will not establish a connection to G Suite.
9. Click **Close** to return to the **Connected apps** list.


### Inspect policies

Cloud App Security policies allow you to control how your users interact with sanctioned SaaS apps. The following policy templates are available to you:

* **Activity policy**: Tracks specific user activities in a connected app
* **Anomaly detection policy**: Tracks for unusual app activity
* **App discovery policy**: Tracks new app installs within your organization
* **Cloud discovery anomaly detection policy**: Tracks unusual behavior in cloud discovery processes
* **File policy**: Tracks file types and file content (for instance, locating personally identifiable information)









### Create a policy





### Perform day-to-day management tasks
































