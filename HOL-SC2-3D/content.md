# Configure Safe Attachments

<!-- Exercise 1 -->
<!--
EXERCISE TODO #2: Set the IntroductionUri and CompletionUri values in the quoted
properties below. Both IntroductionUri and CompletionUri may be relative (within
GitHub) or absolute uris. Remove any values that you don't need, removing the
entire quote if you don't need any of the values. Then delete this comment.

   
>LODSProperties
>* IntroductionUri = 
>* CompletionUri = 
-->

## INTRODUCTION MESSAGE

**Safe Attachments** is a new Advanced Threat Protection feature available in Office 365 which reviews email attachments and takes action on those that are potentially malicious. In this exercise, you will create a Safe Attachment policy to help prevent malicious attachments being circulated within your Exchange Online environment. This policy will redirect potential threats to administrators and remove the attachment from the message before it is delivered.

NOTE: This lab assumes you have previously created an Office 365 E5 trial subscription. You will need two user accounts (Lori and Peter), and one administrator account (Mark).

## COMPLETION MESSAGE

You have now successfully created a Safe Attachments policy.

### Open the Office 365 Admin Center

Log into TBD as **Mark**, with a password of **Passw0rd**. Open **Internet Explorer** and Log into **https://portal.office.com/adminportal/home#/homepage** as **Mark@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes.

### Navigate to the Security & Compliance Center

From the left-hand navigation menu, click **Admin Centers**, and then click **Security & Compliance** to open the Security & Compliance center.

### Navigate to Safe Attachments

In the Security & Compliance center, from the left-hand navigation menu, click **Threat Management** and then click **Safe attachments**.

### Create new Safe Attachments policy

Click the **plus** icon to open the new safe attachments policy dialog box. In the dialog box, name the policy **Replace and Redirect Safe Attachments Policy**.

### Select malware response

In the Safe attachments unknown malware response section, select **Replace** from the list. This will block the attachment but deliver the remaining message content to the recipient.

### Enable redirection

In the Redirect attachment on detection section, select **Enable redirect** and then type Marks email address (eg. **Mark@Contoso.onmicrosoft.com**).

#### :warning: ALERT

Be sure to use the email address from your tenant. It will look something like **Mark@yourdomain.onmicrosoft.com**.

### Apply to all users in the tenant

In the Applied To section, from the drop-down list, choose **The recipient domain is** to open the domain selection dialog box. Double-click **your domain** and then click **OK**. Click **Save** to complete the policy.

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

# Send malicious attachment

## INTRODUCTION MESSAGE

In this exercise you will send a malicious attachment from one user to another via email. This email message will include a subject, body and malicious attachment.

## COMPLETION MESSAGE

You have successfully sent an example malicious attachment via email. 

### Log into Lori's email

Open **Internet Explorer** and Log into **https://outlook.office.com/** as **Lori@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes. Then click **Mail**.

### Create a new message to Peter

Click **New** and type **Peter@yourdomain.onmicrosoft.com** in the To field. In the subject line, type **This is test malware**. In the message box (body of the email), type **This is an example of safe attachments blocking malware**.

### Add malicious attachment

On the menu, click **Attach**, then click **Computer** to open an explorer window. Navigate to **C:\Extras\ExampleAttachment** and select **ExampleAttachment.abc**. Click **Send** to send the message.

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

#### :warning: ALERT

You will come back and review the message later as Safe Attachments can take several minutes to scan the attachment.

# Configure Safe Links

## INTRODUCTION MESSAGE

Safe Links is a new Advanced Threat Protection feature available in Office 365 which allows tenant administrators to block or redirect potentially malicious links to a warning page. When Safe Links recognizes a link that is neither on the block list nor the exemption list, the link is evaluated for malicious properties (such as redirecting to another site). In this exercise, you will create a Safe Links policy to help prevent malicious URLs from being accessed by users in your organizations.

## COMPLETION MESSAGE

You have successfully created a Safe Links policy and enabled it for your test Office 365 tenant.

### Open the Office 365 Admin Center

Log into <Comp> as **Mark**, with a password of **Passw0rd**. Open **Internet Explorer** and Log into **https://portal.office.com/adminportal/home#/homepage** as **Mark@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes.

### Navigate to the Security & Compliance Center

From the left-hand navigation menu, click **Admin Centers**, and then click **Security & Compliance** to open the Security & Compliance center.

### Navigate to Safe links

In the Security & Compliance center, from the left-hand navigation menu, click **Threat Management** and then click **Safe links**.

### Create new Safe Links policy

In the Policies that apply to specific recipients section, click the **plus** icon to open the new safe link policy dialog box. In the dialog box, name the policy **Example Safe Links Policy**.

### Select detection actions

In the Select the action for unknown potentially malicious URLs in messages section, click **On** and select **Use safe attachments to scan downloadable content**. 

### Configure exemption URLs

In the Do not rewrite the following URLs section, in the Enter a valid URL box, type **http://goodurl.contoso.com** and click the **plus** button to add the exemption.

### Apply policy to all users

In the Applied To section, from the drop-down list, choose **The recipient domain is** to open the domain selection dialog box. Double-click **your domain** and then click **OK**. Click **Save** to complete the policy.

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

# Send malicious links

## INTRODUCTION MESSAGE

In this exercise, you will send an email as Lori containing a potentially malicious link from a personal account to act as an attacker. 

## COMPLETION MESSAGE

You have successfully tested the Safe Links policy. 

### Log into Lori's email

Open **Internet Explorer** and Log into **https://outlook.office.com/** as **Lori@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes. Then click **Mail**.

### Send a new message to Peter

Click **New** and type **Peter@<yourdomain>.onmicrosoft.com** in the To field. In the subject line, type **These are some test URLs**. In the message box (body of the email), type **This is an example of safe links redirecting potentially malicious urls http://goodurl.contoso.com http://badurl.contoso.com http://www.bing.com/search?q=test** or click the **TypeText button**. Click **Send** to send the message.

#### :calling: COMMAND TypeText

This is an example of safe links redirecting potentially malicious urls http://goodurl.contoso.com http://badurl.contoso.com http://www.bing.com/search?q=test

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

# Review message containing potentially malicious URL

## INTRODUCTION MESSAGE

In this exercise, you will review the message you sent to Peter in the previous exercise and see what happens when you attempt to access each URL in the message.

## COMPLETION MESSAGE

<!-- -->

### Sign into Peter's email

Open **Internet Explorer** and Log into **https://outlook.office.com/** as **Peter@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes. Then click **Mail**.

### Review Lori's message

In the inbox, you should notice the message from Lori with the subject "**These are some test URLs**". Open the message to review the contents and then click the **Knowledge (bulb) icon**.

#### :bulb: KNOWLEDGE

Hover over each link in the email. The http://goodurl.contoso.com URL should say "**http://goodurl.contoso.com**". However, the Http://badurl.contoso.com URL should have "**SafeLinks**" on the front of the address, redirecting it to be evaluated by Safe Links.

### Click the exempt URL

In the message, click the http://goodurl.contoso.com address then click the **Knowledge (bulb) icon**.

#### :bulb: KNOWLEDGE

Since the good URL was placed on the exception list, you should be taken directly to the site.

### Click the bad URL

In the message, click the http://badurl.contoso.com address then click the **Knowledge (bulb) icon**.

#### :bulb: KNOWLEDGE

Since this URL is not exempt from the Safe Links policy, and it is redirected to another potentially malicious link, a warning page is presented letting you know that the link is unsafe. 

### Continue to the bad URL

In the warning message, click **Continue to site** to proceed to the site anyway. Per the Safe Links policy you created in the previous exercise, this action will be logged for administrative review.

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

# Run URL Trace report

## INTRODUCTION MESSAGE

In this exercise, you will run a URL trace report which will show the URLs redirected or blocked by the safe link policy you created in the previous exercise. 

## COMPLETION MESSAGE

In this exercise, you saw which URLs were discovered by Safe Links and the action which was taken on them. Also, for the blocked URLs, you saw if users continued to access them or not. 

### Open the Office 365 Admin Center

Open **Internet Explorer** and Log into **https://portal.office.com/adminportal/home#/homepage** as **Mark@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes.

### Navigate to the Exchange Admin Center

From the left-hand navigation menu, click **Admin Centers**, and then click **Exchange** to open the Exchange Admin Center.

### Run url trace report

From the left-hand navigation menu, click **mail flow** and then click **url trace** from the top menu. Scroll down to the bottom and click **Search** to run the report. 

### Review the report

Click the **Knowledge (bulb) icon**.

#### :bulb: KNOWLEDGE

In this report, you can see each URL that you clicked in the email sent to Peter, except for the exempt one (http://goodurl.contoso.com). Notice the URL, blocked and clicked through columns. Yuo can see that it shows http://badurl.contoso.com as being blocked but that you clicked through it anyway. 

### Sign out of Office 365

Close the report, sign out of Office 365 and close Internet Explorer.

# Review malicious attachment as intended recipient

<!-- Exercise 3  -->

## INTRODUCTION MESSAGE

In this exercise, you will review the message you sent to Peter in a previous exercise. With the Safe Attachment policy you created in the first exercise, the intended recipient should receive the message with the original attachment removed.

## COMPLETION MESSAGE

You have now seen the user experience when Safe Attachments determines an attachment is malicious. 

### Sign into Peter's email

Open **Internet Explorer** and Log into **https://outlook.office.com/** as **Peter@yourdomain.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes. Then click **Mail**.

### Review Lori's message

In the inbox, you should notice a message from Lori. Open the message to review the contents and then click the **Knowledge (bulb) icon**.

#### :bulb: KNOWLEDGE

You can see the message subject and body was received but the attachment has been removed.

### Sign out of Office 365

Sign out of Office 365 and close Internet Explorer.

# Review message as an administrator


## INTRODUCTION MESSAGE

Since the Safe Attachment policy you created in the first exercise was configured to redirect malicious attachments to the administrator, in this exercise you will view what that redirected message looks like after it is sent to Mark.  

## COMPLETION MESSAGE

You have seen the administrator experience when a malicious attachment is redirected. 

### Sign into Mark's email

Open **Internet Explorer** and Log into **https://outlook.office.com/** as **Mark@<yourtenant>.onmicrosoft.com** from the Office 365 tenant you previously created for testing purposes. Then click **Mail**.



# Run Advanced Threat Protection by Disposition report

<!-- Exercise 5  -->

## INTRODUCTION MESSAGE

<!-- -->

## COMPLETION MESSAGE
<!-- -->


#### :bulb: KNOWLEDGE

<!--
TASK TODO #3: Replace this comment with any knowledge text that you want
displayed when a student clicks on the Knowledge button. Knowledge text must
not be required for students to complete a task. It is used to provide students
with additional details, hints, or alternative ways to perform a task. If you
do not have any knowledge text to display for this task, delete this comment
and the KNOWLEDGE heading before it.
--> 

#### :camera: SCREENSHOT

<!--
TASK TODO #4: In the quoted properties below, set the Uri property to the uri of
a screenshot you want to link to this task. This can be a relative (within
GitHub) or absolute uri. Then set the ShowAutomatically property to one of the
following:
- No, if you only want the screenshot to appear when the student clicks on the
camera button;
- Once, if you want the screenshot to appear automatically the first time the
student advances to this task; or
- EveryTime, if you want the screenshot to appear automatically every time the
student advances or returns to this task.

Once you have set the screenshot properties, delete this entire comment.

If you do not have a screenshot to associate with this task, delete the
SCREENSHOT heading above this comment as well as this comment and the quote
below it.
-->  
>LODSProperties
>* Uri = 
>* ShowAutomatically = No|Once|EveryTime

#### :movie_camera: VIDEO

<!--
TASK TODO #5: In the quoted properties below, set the Uri property to the uri of
a video you want to link to this task. This can be a relative (withing GitHub)
or absolute uri. Then set the ShowAutomatically property to one of the
following:
- No, if you only want the video to appear when the student clicks on the video
camera button;  w 
- Once, if you want the video to appear automatically the first time the
student advances to this task; or
- EveryTime, if you want the video to appear automatically every time the
student advances or returns to this task.

If you want the video to appear in a separate dialog, set ShowInDialog to true;
otherwise, set it to false. 

Once you have set the video properties, delete this entire comment.

If you do not have a video to associate with this task, delete the VIDEO
heading above this comment as well as this comment and the quote below it.
-->
>LODSProperties
>* Uri = 
>* ShowAutomatically = No|Once|EveryTime
>* ShowInDialog = true|false

#### :calling: COMMAND TypeText|PowerShell|PowerShellWithUI|Shell|ShellWithUI
