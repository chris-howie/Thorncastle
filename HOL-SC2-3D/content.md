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

## E1 INTRODUCTION MESSAGE

Safe Attachments is a new Advanced Threat Protection feature available in Office 365 which allows tenant administrators to check if emaill attachments are malicious and take action on those that are potentially malicious. In this exercise, you will create a Safe Attachment policy to help prevent malicious attachments being circulated within your Exchange Online environment, including redirecting potential threats to administrators and replacing the original attachment sent to the recipient with a removal notification.

NOTE: This lab assumes you have previously created an Office 365 E5 trial subscription. You will need two user accounts (Lori and Peter), and one administrator account (Mark).

## E1 COMPLETION MESSAGE

You have now successfully configured a Safe Attachments policy.

### Open the Office 365 Admin Center

Log into <Comp> as **Mark**, with a password of **Passw0rd**. Open **Internet Explorer** and Log into **https://portal.office.com/adminportal/home#/homepage** using the Office 365 tenant you previously created for testing purposes.

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

Be sure to use the email address from your tenant. It will look something like **Mark@<yourtenant>.onmicrosoft.com**.

### Apply to all users in the tenant

In the Applied To section, from the drop-down list, choose **The recipient domain is** and then click **add condition** to open the domain selection dialog box. Double-click **your domain** and then click **OK**. Click **Save** to complete the policy.

# Send malicious attachment

<!-- Exercise 2 -->

## E2 INTRODUCTION MESSAGE

In this exercise you will attempt to send a malicious attachment from one user to another. This message will include a subject, body and malicious attachment. 

## E2 COMPLETION MESSAGE

You have successfully sent an example malicious attachment via email. 

# Review malicious attachment as intended recipient

<!-- Exercise 3  -->

## E3 INTRODUCTION MESSAGE

In this exercise, you will review the message you sent in the previous exercise. With the Safe Attachment policy you created in the first exercise, the intended recipient should receive the message with the original attachment removed and replaced with an indication that it was removed. 

## E3 COMPLETION MESSAGE

You have now seen the user experience when Safe Attachments determines an attachment is malicious. 

# Review message as an administrator

<!-- Exercise 4  -->

## E4 INTRODUCTION MESSAGE

Since the Safe Attachment policy you created in the first exercise was configured to redirect malicious attachments to the administrator, in this exercise you will view what that redirected message looks like. 

## E4 COMPLETION MESSAGE

<!-- -->

# Run Advanced Threat Protection by Disposition report

<!-- Exercise 5  -->

## E5 INTRODUCTION MESSAGE

<!-- -->

## E5 COMPLETION MESSAGE
<!-- -->

# Configure Safe Links  
<!-- Exercise 6  -->
## E6 INTRODUCTION MESSAGE
<!-- -->

## E6 COMPLETION MESSAGE
<!-- -->

# Send malicious links
<!-- Exercise 7  -->
## E7 INTRODUCTION MESSAGE
<!-- -->

## E7 COMPLETION MESSAGE
<!-- -->

# Review message containing malicious links
<!-- Exercise 8  -->
## E8 INTRODUCTION MESSAGE
<!-- -->

## E8 COMPLETION MESSAGE
<!-- -->

# Run URL Trace report
<!-- Exercise 9  -->
## E9 INTRODUCTION MESSAGE
<!-- -->

## E9 COMPLETION MESSAGE
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
camera button;
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

<!--
TASK TODO #6: In the heading above, choose the command type (TypeText,
PowerShell, PowerShellWithUI, Shell, ShellWithUI) appropriate for this command
and remove the others. If the command type is PowerShell or PowerShellWithUI,
leave the "PowerShell" language specifier that is next to the code block
opening enclosure; otherwise, remove the language specifier and simply leave
the code block opening enclosure with nothing after it. Then, enter the
appropriate command text in the code block below.

Once you have set up the command type and code block properly, delete this
entire comment.

If you do not have a command to associate with this task, delete the COMMAND
heading above this comment as well as this comment and the code block below it.
-->
```
# Replace this line with the PowerShell command, shell command, or text to type.
# If this command is anything other than PowerShell or PowerShellWithUI, remove
# the "PowerShell" label at the beginning of this code block.
```

#### :computer: ACTIONS

<!--
TASK TODO #7: In the quoted properties below, set the VM property to one of the
following:
- NoAction, if you don't want to change the active VM in the lab;
- VNName, if you want to select a different VM in the lab as the active VM
(Note that you must enter the name of the VM in place of the "VMName" string in
order for this to work).

Then set the FloppyDrive property to one of the following:
- NoAction, if you don't want to change the state of the virtual floppy drive
in the active VM;
- FloppyName, if you want to insert a different floppy disk into the virtual
floppy drive in the active VM (Note that you must enter the name of the floppy
disk in place of the "FloppyName" string in order for this to work);
- Eject, if you want to eject the floppy disk in the virtual floppy drive in
the active VM.

Then set the DvdDrive property to one of the following:
- NoAction, if you don't want to change the state of the virtual DVD drive
in the active VM;
- DvdName, if you want to insert a different DVD disk into the virtual DVD
drive in the active VM (Note that you must enter the name of the DVD disk
in place of the "DvdName" string in order for this to work);
- Eject, if you want to eject the DVD disk in the virtual DVD drive in the
active VM.

Once you have configured the actions for the task, delete this entire comment.

If you do not want to take any of these actions with this task, delete the
ACTIONS heading above this comment as well as this comment and the quote below
it.
-->
>LODSProperties
>* VM = NoAction|VMName
>* FloppyDrive = NoAction|FloppyName|Eject
>* DvdDrive = NoAction|DvdName|Eject

<!--
NEW TASK TODO #1: If you want to add another task, copy and paste the contents of
the task template you want to use over this comment. You can find the task
templates here:
https://github.com/LearnOnDemandSystems/idl-md/blob/master/templates
-->

<!--
NEW EXERCISE TODO #1: If you want to add another exercise, copy and paste the
contents of the exercise template you want to use over this comment. You can find
the exercise templates here:
https://github.com/LearnOnDemandSystems/idl-md/blob/master/templates
-->