# Smart Alarm Clock - **craft ai** getting started app #

Welcome to the **Smart Alarm Clock** (**SAC** for short) [**craft ai**](http://craft.ai) _getting started_ application.

## Requirements ##
1. Install [Python 2.7](https://www.python.org) on your computer,
2. Install [pip](https://pip.pypa.io/en/latest/installing.html).

## Forking the GitHub repository ##
First, you will need to fork this GitHub repository of the app, so that you can manipulate the behaviors and actions.

To do so, go to [github.com/craft-ai/SmartAlarmClock](https://github.com/craft-ai/SmartAlarmClock), log in with your GitHub account and click on the **Fork** button, in the top right corner of the page.

You can now clone your fork on your machine using your favorite GitHub client. We'll call `<sac_dir>` the destination path of the local clone.

## Run the application locally ##
Before making any changes, let's make sure that the **SAC** application is running without any problem.
A little bit of customization will be needed here.

### Exposing your localhost on the Internet ###
Since the **SAC** application needs to communicate with the **craft ai** server, you must expose your localhost on the Internet. This is exactly what [ngrok](https://ngrok.com/) allows to do. We'll need at least **ngrok v2.0**.

[Download](https://ngrok.com/download) ngrok and unzip the executable file (eg. `ngrok.exe` on Windows) to `<sac_dir>`.

> Mac users can also install ngrok using [homebrew](http://brew.sh/), but as we need at least the 2.0 version that is not open source [homebrew cask](https://github.com/caskroom/homebrew-cask) can install it using `brew cask install ngrok`.

### User configuration ###
The following information will be required to run the application:

- your GitHub username (more precisely, the namespace in which you forked the **SAC** GitHub project)
- the name of your fork (default: SmartAlarmClock)
- the branch of your demo.sac fork you want to use (default: master)

### Google services credentials ###
Since the **SAC** app uses some Google services you will need to give it access to the related API by following the steps below:

- go to [https://console.developers.google.com](https://console.developers.google.com)
- log in with your Google account (create one if necessary)
- create a project with the name of your choice
- open the **APIs & auth** menu
- go to the **APIs** sub-menu
	- in the **Google Apps APIs** category, enable the following:
    	- Calendar API
    	- Gmail API
- go to the **Credentials** sub-menu
	- add a new client ID:
	    - click on **Create new Cliend ID**
	    - choose **Web application** as application type
	    	- click on **Configure Consent Screen**
	    	- put **SmartAlarmClock** as Product Name
	    	- click on **Save**
	    - empty the **Authorized JavaScript origins** field
	    - put **http://localhost:8080/auth** in the **Authorized redirect URIs** field
	    - click the **Create Client ID** button

Keep the generated _Client ID_ and _Client secret_ handy, you will need them later.

There is no need to enable billing for Google APIs to try out the **SAC** app.

### App configuration ###
You will also need to have an _Application ID_ and an _Application secret_ for your version of the **SAC** application. Those are generated by **craft ai**:

- go to the [craft ai editor](http://editor.craft.ai/)
- log in with your GitHub account - you'll need to have a [_beta_ access](http://www.craft.ai/#newsletter) for this step to work
- click on the **add projects** button and check the box on the right of the project corresponding to your fork of the project (something along the lines of **<yourGitHubName>/SmartAlarmClock**)
- click on the "Add 1 project" button at the bottom of the list. The project will be added to your workspace and you can select it to start editing it
- in the project explorer that appears on the left of the page, click on the **cog** button on the right of the project name

You will end up on the **settings** page which will display the `Application ID` and the `Application secret` needed at the first run of the application.

### Launch the Smart Alarm Clock ###
Install the requirements by running `pip install -r requirements.txt` from `<sac_dir>`

Launch the application by running the command `python local_demo.py` from `<sac_dir>` and fill in the fields with the data from the previous steps. These fields will be saved in a configuration file, you won't have to input everything the next time you run the application.

In your browser, go to [http://localhost:8080](http://localhost:8080). The Smart Alarm Clock should show up and ask you to log in with a Google Account.

## Edit the behavior trees ##
You can edit the behaviors by logging into the [craft ai editor](http://editor.craft.ai/) with your GitHub account and opening your **SAC** project.
In the project explorer, click on one of the behavior tree (`*.bt` file) to open it in the editor.

## Details ##

### Environment Variables ###

The demo is configured using the following environment variables:

- `CRAFT_DEMO_SAC_URL`, the public URL of the web app
- `CRAFT_DEMO_SAC_WS_URL`, the websocket URL of the web app
- `CRAFT_DEMO_SAC_PORT`, the port to which the web app servers listens
- `CRAFT_DEMO_SAC_USER`, the GitHub namespace hosting the GitHub project (either the GitHub username or the organization name to which the project belongs)
- `CRAFT_DEMO_SAC_PROJECT`, the GitHub project containing the associated BT files
- `CRAFT_DEMO_SAC_VERSION`, the version branch of the GitHub project
- `CRAFT_DEMO_SAC_ACTIONS_URL`, the URL of the web app
- `CRAFT_DEMO_SAC_DEPLOYMENT_DIR`, the path, in the runtime container, of the compiled BTs
- `CRAFT_DEMO_SAC_GOOGLE_CLIENT_ID`, The SAC application ID
- `CRAFT_DEMO_SAC_GOOGLE_CLIENT_SECRET`, The SAC application secret
- `CRAFT_DEMO_SAC_GOOGLE_CLIENT_ID`, Google API client id
- `CRAFT_DEMO_SAC_GOOGLE_CLIENT_SECRET`, Google API client secret
- `CRAFT_DEMO_SAC_GOOGLE_API_KEY`, Google API key
