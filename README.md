
# ThousandEyes

---------

<kbd>
<a href="https://support.xmatters.com/hc/en-us/community/topics">
   <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</a>
</kbd>

---------


# Pre-Requisites
* ThousandEyes [account](https://www.thousandeyes.com/signup)
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

# Files
* [ThousandEyes.zip](ThousandEyes.zip) - The Workflow containing the scripts and message templates

# How it works
Alerts in ThousandEyes are set up to fire a webhook when they fire. The webhook targets the xMatters Inbound Integration script, which transforms the payload into the correct format and creates the event. The recipients defined in the form layout are targeted for notification. Alternatively [subscriptions](http://help.xmatters.com/OnDemand/userguide/receivingalerts/subscriptions/howtousesubscriptions.htm) can be set up to notify the desired parties based on values in the alert. 

# Installation
This section outlines the steps needed to get the integration installed. 

## xMatters set up
1. Load in the [ThousandEyes.zip](ThousandEyes.zip) workflow by clicking Import Plan from the Workflows section 
2. On the ThousandEyes plan, click Edit > Integration Builder and expand the Inbound Integrations. 
3. Click the `Inbound from ThousandEyes` link and scroll down to copy the Url. Save for later. 
4. Click on the Forms tab and click Edit > Layout next to the Send Alert form. 
5. Enter the default recipients to target when this alert fires. Alternatively [subscriptions](http://help.xmatters.com/OnDemand/userguide/receivingalerts/subscriptions/howtousesubscriptions.htm) can be set up based on matching the incoming properties. 

## ThousandEyes set up
1. Login to ThousandEyes and navigate to the Alerts section. Expand the appropriate alert and click the Notifications tab. 
2. Click the Edit webhooks in the Webhooks section and click Add New Webhook. 
3. Name it `xMatters` and paste in the url from above. If basic authentication is required, see the note below. 


**Basic Authentication** 

To set up Basic Authentication follow these steps:
1. In xMatters, in the `Inbound from ThousandEyes` script, change the authentication method to Basic Authentication. 
2. Create a user in xMatters and note the password. Grant the `Standard User`, `Web Service User` and `Full Access User` roles to this user. 
3. On the Workflows section next to the ThousandEyes workflow, click edit > Access Permissions. Add the user just created to the list. 
4. Click the Forms entry in the Edit drop down and in the `Send Alert` form, click Web Service Only > Sender Permissions and add the user again. 

Next, in ThousandEyes:

1. Click the `Enable Basic HTTP Authentication` link on the Edit webhooks dialog in ThousandEyes for the xMatters Webhook.
2. Enter the username and password for the xMatters user created above. 


# Testing
Take down a website or add a test for a bogus website on an Alert and add the xMatters Webhook Notification. This will trigger the webhook which will run the script in `Inbound from ThousandEyes` and fire an event to notify the recipients defined on the `Send Alert` form. 


# Troubleshooting
Test the webhook and ensure a new entry is added to the activity stream for `Inbound from ThousandEyes`. If not, verify the webhook url is correct. 
If testing the webhook does add an entry to the activity stream, review the activity stream for any errors or other messages. 

