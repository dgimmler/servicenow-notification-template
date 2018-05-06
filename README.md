# ServiceNow Centralized Notifications Template
## Introduces mail scripts and config page to provide a centralized template for ServiceNow notifications

### Intro:
![Screenshot](https://github.com/dgimmler/servicenow-notification-template/blob/master/Email%20Body%20Screenshot.png?raw=true)

While ServiceNow's email templates provide a great way to create reusable templates for multiple emails, I always felt it lacked a centralized way to manage notification branding. In my customer engagements I always tried to provide consistency in the look and feel of notifications, which often meant copying and pasting the same base html between email templates or notifications themselves. This meant that whenever we wanted to change the overal branding we had a lot of manual work to do.

This update sets provides a set of mail scripts and a config page to provide a generic email template that looks great, can be set to as many or as little emails as needed and most of all, can be modified in one place!

![Screenshot](https://github.com/dgimmler/servicenow-notification-template/blob/master/Config%20Page%20Screenshot.png?raw=true)

### Installation:
1. Download the update set file (update_set_notification_template.xml)
2. In your target ServiceNow instance, select "Import Update Set from XML" under "System Update Sets -> Retrieved Update Sets". Selected the downloaded XML.
3. Preview and commit the update set.
4. The following features are installed:
- Mail scripts to provide generic email template
- Module link under System Notification to central notification config page
- System properties with default values as well as system properties category

### Configuration:

#### Adding template to email notification:
Either under the email notificaiton form itself or else on an email template form, make the following changes to the body html:
- Make sure ${mail_script:notification_header} is the very first line
- Make sure ${mail_script:notification_footer} is the very last line

Anything between the two mail scripts will be included in the body. The lines can be added to existing html as long as they remain the first and last lines of the html body respectively.

#### Configuring branding
1. Navigate to System Notification -> Notification Template Config
2. Modify the config page as needed and save the form!

NOTES:
- I strongly recommend adding the image to be used as the logo to the images database in ServiceNow to ensure there are no issues with retrieving the image
- All size, width and color values take in valid CSS property values. If they work in general CSS files, they should work here. Default values and examples are provided to assist in understanding what values will work.

#### Advanced Configuration
The template utilizes the mail scripts notification_header and notification_footer. These mail scripts provide the html for the generic template. Feel free to modify the html added by these scripts to further customize the template. Even if the generic template provided is really too generic, the scripts will still allow you to centrally manage the look and feel of mutliple email notifications in one place.
