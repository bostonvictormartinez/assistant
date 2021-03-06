---

copyright:
  years: 2015, 2020
lastupdated: "2020-01-29"

subcollection: assistant

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Integrating with Slack
{: #deploy-slack}

Slack is a cloud-based messaging application that helps people collaborate with one another.
{: shortdesc}

After you configure a dialog skill and add it to an assistant, you can integrate the assistant with Slack.

When integrated, depending on the events that you configure the assistant to support, your assistant can respond to questions that are asked in direct messages or in channels where the assistant is directly mentioned. 

## Adding the Slack integration
{: #deploy-slack-task}

1.  From the Assistants page, click to open the assistant tile that you want to deploy.

1.  From the Integrations section, click **Add integration**.

1.  Click **Slack**.

1.  Follow the instructions that are provided on the screen to complete the integration process.

    Choose one or more of the following subscription events to support:

    - `message.im`: The assistant responds when someone starts a direct message with the assistant.
    - `app_mentions`: The assistant responds when someone mentions the assistant by name in a channel.

If you want to follow along as someone else walks through the deployment steps, watch this video.

<iframe class="embed-responsive-item" id="youtubeplayer" title="Walkthrough of the Slack deployment steps" type="text/html" width="640" height="390" src="https://www.youtube.com/embed/RBGBPJ8h4HQ?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

Duration: 9.5 minutes

## Dialog considerations
{: #deploy-slack-dialog}

The rich responses that you add to a dialog are displayed in a Slack channel as expected, with the following exceptions:

- **Connect to human agent**: This response type is ignored.

- **Image**: An image title is required. If you do not provide a title, the image is not displayed.

- **Option**: This response type shows a list of options that the user can choose from.

  - A title is **required** and is displayed before the list of options.
  - A desciption is not displayed, whether you specify one or not.
  - After a user clicks one of the buttons, the button choices disappear and are replaced by the user input generated by the user's choice. If you include multiple response types in a single response, position the option response type last. Otherwise, the output will contain a mix of responses and user inputs that might confuse the user.

- **Pause**: This response type pauses the assistant's activity in the Slack channel. However, no visible indicator is shown to indicate that the assistant is paused, whether you choose to show typing or not.

See [Rich responses](/docs/assistant?topic=assistant-dialog-overview#dialog-overview-multimedia) for more information about response types.

## Chatting with the assistant
{: #deploy-slack-try}

To start a chat with the assistant, complete the following steps:

1.  Open Slack, and go to the workspace associated with your app.
1.  Click the application that you created from the Apps section.
1.  Chat with the assistant.

The Welcome node of your dialog is not processed by the Slack integration. The welcome message is not displayed in the slack channel like it is in the "Try it out" pane or in the Preview Link integration web page. It is not triggered from here because nodes with the `welcome` special condition are skipped in dialog flows that are started by users. Slack waits for the user to initiate the conversation. If you need to set default values for context variables at the start of your conversation, do not set them in the welcome node. See [Starting the dialog](/docs/assistant?topic=assistant-dialog-start) for more information.
{: note}

The dialog flow for the current session is restarted after 60 minutes of inactivity (5 minutes for Lite and Standard plans). This means that if a user stops interacting with the assistant, after 60 (or 5) minutes, any context variable values that were set during the previous conversation are set to null or back to their default values.
