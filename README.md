# TagUI
TagUI is a general purpose tool for automating web interactions ~ http://tebel.org

![Sample Automation Flow](https://raw.githubusercontent.com/tebelorg/Tump/master/tagui_flow.gif)

A sample automation flow to automate mass account registrations in 30 seconds - 1. recording sequence of steps, 2. editing to wait for a few seconds, 3. playing the automation flow (csv datatables supported for datasets)

# Why This
The goal of web automation is to reproduce cognitive interactions that you have with certain websites so that your laptop or server can do it for you, base on your preferred schedule or conditions. TagUI helps you rapidly automate your repetitive or time-critical tasks - use cases include process automation, data acquisition and testing of web apps.

### FEATURES
- natural language with JavaScript support
- Chrome extension for recording steps
- object repositories and datatables
- auto-wait XPath/CSS element selector
- live mode to try steps or code in real-time
- run by schedule, command line, REST API
- support outgoing API calls to webservices

### HOW IT WORKS
TagUI converts your intentions in simple natural language into lines of working JavaScript code that perform web automation. Under the hood, it uses CasperJS, PhantomJS & SlimerJS. As an example, TagUI will instantly convert the automation flow below into 100+ lines of JavaScript code and automatically perform the steps to download a Typeform report. This makes it very easy for rapid prototyping, deployment and maintenance of web automation.

```
https://www.typeform.com
click login
type username as user@gmail.com
type password as 12345678
click btnlogin
hover Test Event
click action results tooltip
click section_results
download https://admin.typeform.com/form/2592751/analyze/csv to report.csv
```

The automation flow can be triggered from scheduling, command line, URL, REST API, email etc. Everything happens headlessly in the background without seeing any web browser, so that you can continue using the computer or server uninterrupted. Running on a visible web browser is also supported, using Firefox browser and SlimerJS (see firefox option below). Outgoing API calls can be made with a single line to integrate with other downstream applications.

If you know JavaScript coding and want to be more expressive, you can even use JavaScript directly in the flow. If not, you will still enjoy friendly but powerful features such as repositories to store your reusable objects, datatables for batch automation, and a Chrome extension which creates automation flows by recording your actions. For rapid prototyping, there's also an interactive live mode for trying out TagUI steps or JavaScript code in real-time.

This is a full-feature and free open-source tool, so there's nothing to upgrade to or any paid subscription. To feedback suggestions or bugs, kindly [raise an issue](https://github.com/tebelorg/TagUI/issues) or email ken@tebel.org. Originally developed by a test automation engineer to avoid writing code when automating web interactions.

# Set Up
TagUI is in v1.5 and runs on macOS, Linux, Windows ([link to release notes](https://github.com/tebelorg/TagUI/releases))

### PACKAGED INSTALLATION
Easiest way to use TagUI - no setup is needed, all dependencies are packaged in

Platform|macOS|Linux|Windows|Node.js
:------:|:---:|:---:|:-----:|:-----:
Package|[unzip and run](https://raw.githubusercontent.com/tebelorg/Tump/master/TagUI_macOS.zip)|[unzip and run](https://raw.githubusercontent.com/tebelorg/Tump/master/TagUI_Linux.zip)|[unzip and run](https://raw.githubusercontent.com/tebelorg/Tump/master/TagUI_Windows.zip)|[npm install tagui](https://www.npmjs.com/package/tagui)

Optional - configure web browser settings in tagui_config.txt, such as browser resolution, step timeout of 10s etc

### MANUAL INSTALLATION
If you prefer to download dependencies manually from respective websites

1. PhantomJS (headless scriptable web browser) - http://phantomjs.org
2. CasperJS (navigation/testing for PhantomJS) - http://casperjs.org
3. SlimerJS (scriptable web browser for Firefox) - https://slimerjs.org
4. TagUI (general purpose web automation tool) - https://git.io/vMCTZ
5. PHP (only required for manual Windows setup) - http://windows.php.net

Tip - for manual Windows setup, 1. set SLIMERJS_EXECUTABLE environment variable to point to slimerjs.bat, 2. place [GNU utilities](http://unxutils.sourceforge.net) (gawk/tee/sort/head/tail), [curl ssl](https://curl.haxx.se) in tagui\src\unx folder, 3. add phantomjs\bin, casperjs\bin, php folders to path

# To Use
### COMMAND LINE
```
./tagui flow_filename option(s) for macOS/Linux, tagui flow_filename option(s) for Windows
```
- Flow filename (and its .csv) can be a local file or the URL of an online file
- Automation flow filename can have no extension, .gui or .txt file extension
- Objects, keywords, datatables can be defined in flow_filename.csv (optional)

Option|Purpose
:----:|:------
firefox|run on visible Firefox web browser instead of invisible browser (first install [Firefox](https://www.mozilla.org/en-US/firefox/new/))
report|generate a web report for easy sharing of run results (default is only a text log file)
debug|show run-time backend messages from PhantomJS for detailed tracing and logging
quiet|run without output except for explicit output (echo / show / check / api / errors etc)
test|professional testing using [CasperJS assertions](http://docs.casperjs.org/en/latest/modules/tester.html) (TagUI dynamic tx('selector') usable)
input(s)|add your own parameter(s) to be used in your automation flow as variables p1 to p9

Tip - to run tagui from anywhere in macOS/Linux, use ln -sf /full_path/tagui/src/tagui /usr/local/bin/tagui to create symbolic link. To run tagui from anywhere in Windows, add tagui/src [folder to path](http://lmgtfy.com/?q=add+to+path+in+windows). Then tagui will be accessible from any folder. If you have issue running visible automation using Firefox/SlimerJS [check this setting](https://docs.slimerjs.org/current/installation.html#using-unstable-version-or-very-old-versions-of-firefox).

### BY SCHEDULING
To schedule an automation flow in crontab (macOS/Linux), for example at 8am daily
```
0 8 * * * /full_path_on_your_server/tagui flow_filename option(s)
```

Tip - for Windows, use Task Scheduler instead (search schedule from Start Menu)

### CHROME EXTENSION
Download from [Chrome Web Store](https://chrome.google.com/webstore/detail/tagui-web-automation/egdllmehgfgjebhlkjmcnhiocfcidnjk/) to use TagUI Chrome web browser extension for recording automation flows. TagUI Chrome extension is based on [Resurrectio tool](https://github.com/ebrehault/resurrectio) and records steps such as page navigation, clicking web elements and entering information. To start recording your automation flows, simply click TagUI icon on your Chrome toolbar. Right-click for shortcuts to various TagUI steps, such as capturing webpage or element screenshot.

### FLOW SAMPLES
Following automation flow samples ([tagui/src/samples folder](https://github.com/tebelorg/TagUI/tree/master/src/samples)) are included as part of this repository

Flow Sample |Purpose
:-----------|:------
1_yahoo|searches github on Yahoo and captures screenshot of results
2_twitter|goes to a Twitter page and saves some profile information
3_github|goes to a GitHub page and downloads the repo using 2 ways
4_conditions|goes through examples of using conditions in natural language
5_repositories|shows using repositories on Russian social media site VK.com
6_datatables|set of flows uses datatables to retrieve and act on GitHub info
7_testing|shows how to use check step and CasperJS test assertions
8_hastebin|shows uploading of automation flow result to hastebin.com

# Cheat Sheet
### AUTOMATION WORKFLOW
- What happens behind the scenes when you run an automation flow

![TagUI Flowchart](https://raw.githubusercontent.com/tebelorg/TagUI/master/src/media/flowchart.png)

### STEPS DESCRIPTION
- TagUI auto-waits for a webpage element to appear and interacts with it as soon as it appears
- Element identifier can be auto-recorded using TagUI Chrome extension, or [found from web browser](https://help.surveygizmo.com/help/how-to-find-element-ids-to-use-with-javascript)
- TagUI auto-selects provided identifier in this order - xpath, css, id, name, class, title, aria-label, text(), href

Step|Parameters (separator in bold)|Purpose
:---|:-----------------------------|:------
tap / click|element to click|click on an element
hover / move|element to hover|move cursor to element
type / enter|element to type ***as*** text to type |enter element as text
select / choose|element to select ***as*** option value to select|choose dropdown option
read / fetch|element to read (page = webpage) ***to*** variable name|fetch element text to variable
show / print|element to read (page = webpage, ie raw html) |print element text to output
save|element (page = webpage) ***to*** optional filename|save element text to file
echo|text (in quotation marks) and variables|print text/variables to output
dump|text and variables ***to*** optional filename|save text/variables to file
snap|element (page = webpage) ***to*** optional filename|save screenshot to file
download|url to download ***to*** filename to save|download from url to file
receive|url keyword to watch ***to*** filename to save|receive resource to file
wait|optional time in seconds (default is 5 seconds)|explicitly wait for some time
live|try steps or code interactively in invisible browser|enter live mode ([firefox pending](https://github.com/laurentj/slimerjs/issues/188))
check|condition **&#124;** text if true **&#124;** text if false (text in quotes)|check condition and print result
frame|frame name **&#124;** subframe name if any|run next step in frame/subframe
popup|url keyword of popup window to look for|run next step in popup window
dom|javascript code for document object model|run code in dom context
api|full url (including parameters) of api call|call api and print response
//|user comments (ignored during execution)|add user comments

Tip - in general, '+variable+' can be used where text is expected to use variables. xpath is an expressive way to identify web elements. if you are writing xpath for element identifier, use double quotes for text //\*[@title="Login"]

### CONDITIONS EXAMPLES
- Conditions can be expressed in natural language (optional brackets) or [JavaScript](https://www.w3schools.com/js/)
- Write text in quotation marks (either " or ' works) to differentiate from variable names
- Conditions if / for / while apply to the next step and async wait auto-disables in loops

Condition (in natural language)|JavaScript
:------------------------------|:---------
example - if day equals to "Friday"| if (day == "Friday")
example - if menu contains "fruits"| if (menu.indexOf("fruits")>-1)
example - if A more than B and C not equals to D | if ((A > B) && (C != D))
example - for n from 1 to 4 | for (n=1; n<=4; n++)
example - while cupcakes equal to 12| while (cupcakes == 12)
contain|.indexOf("text")>-1
not contain|.indexOf("text")\<0
equal to|==
not equal to|!=
more than / greater than / higher than|>
more than or equal to / greater than or equal to / higher than or equal to|>=
less than / lesser than / lower than|<
less than or equal to / lesser than or equal to / lower than or equal to|<=
and|&&
or|**&#124;&#124;**

Tip - when using contain / equal conditions, you can write with or without s behind

### REPOSITORIES
- Repositories help to make objects or steps reusable and improve readability
- Save repository file with same name as your flow filename and with .csv behind
- Repository must have 2 columns, for example below (headers up to you to name)
- Using \`object\` in your flow replaces it with its definition (which can contain objects)
- For example, \`type email\` becomes type user-email-textbox as user@gmail.com

OBJECT|DEFINITION
:-----|:---------
email|user-email-textbox
create account|btn btn--green btn-xl signup-btn
type email|type \`email\` as user@gmail.com
  
### DATATABLES
- Datatables extend the power of repositories files to manage batch automation
- Datatable has 2 or more columns, for example below (headers up to you to name)
- Data-centric approach with rows representing data fields (usually row = test case)
- TagUI loops through each column to automate using values from different datasets
- Eg, echo "TESTCASE - \`testname\`" in your flow shows TESTCASE - Trade USDSGD

TEST TRADES|TEST #1|TEST #2|TEST #3
:----------|:------|:------|:------
testname|Trade USDSGD|Trade USDJPY|Trade EURUSD
username|test_account|test_account|test_account
password|12345678|12345678|12345678
currency-pair|USDSGD|USDJPY|EURUSD
size|10000|1000|100000
direction|BUY|SELL|BUY

# Developers Reference
### API
Automation flows can also be triggered via REST API. TagUI has an API service and runner for managing a queue of incoming requests via API. To set up, add a crontab entry on your server with the desired frequency to check and process incoming service requests. Below example will check every 15 minutes and run pending flows in the queue.
```
0,15,30,45 * * * * /full_path_on_your_server/tagui_crontab
```

To call an automation flow from your application or web browser, use below API syntax. Custom input(s) supported. Automation flows can also be triggered from emails using the API. For email integration, [install Tmail](https://github.com/tebelorg/Tmail). Its main job is an open-source mailbot to act on incoming emails or perform mass emailing; its part-time job is delivering emails by API.
```
your_website_url/tagui_service.php?SETTINGS="flow_filename option(s)"
```

Besides integrating with web applications, TagUI can be extended to integrate with hardware (eg Arduino or Raspberry Pi) for physical world interactions or machine learning service providers for AI decision-making ability. Input parameters can be sent to an automation flow to be used as variables p1 to p9. Output parameters from an automation flow can be sent to your Arduino or application REST URL (see flow samples 3_github and 6C_datatables for examples).

For making outgoing API calls in your automation flow, to feed data somewhere or send emails etc, use the api step followed by full URL (including parameters) of the API call. Response from the API will be printed to output and saved in api_result variable. Emails with run-time variables can be sent directly from your flow with a single line.

### TESTING
The step check allows simple testing of conditions. For professional test automation, CasperJS comes with a tester module for unit and functional testing purpose. To use the advanced testing features, run TagUI with the test option.

CasperJS test scripts are inherently different in structure and syntax from its usual automation scripts. With the test option, TagUI automatically sets up your automation flow to work as a test script. CasperJS will output a XUnit XML file, which is compatible with continuous integration tools such as Jenkins. Running together with the report option outputs a web report of the test execution for easy sharing.

TagUI allows you to reuse the same flow for testing or automation by running it with or without the test option. Below are examples of CasperJS test assertions written in JavaScript code that can be used directly in your automation flow (after navigating using usual flow steps). As this is direct CasperJS code, there is no auto-wait. You can use the wait step to explicitly wait for a few seconds for steps which take a long time for web-server to respond.
```javascript
test.assertTextExists('ABOUT','Check for ABOUT text');
test.assertSelectorHasText(tx('header'), 'Interface automation','Check for phrase in header element');
```

For the list of 30+ expressive test assertions built into CasperJS, [click here](http://docs.casperjs.org/en/latest/modules/tester.html). To know more about CasperJS testing framework, [click here](http://docs.casperjs.org/en/latest/testing.html). As TagUI allows you to write JavaScript code directly within the automation flow, advanced testing or coding techniques that can be implemented in CasperJS should work directly within your flow.

TagUI recognizes most JavaScript code. In the rare event you get an error saying that it cannot understand the step for your JavaScript line, kindly raise an issue or modify the source code (tagui_parse.php is where interpretation of natural language to CasperJS JavaScript code takes place). Alternatively, you can use the undocumented step js to explicitly declare that whatever follows on that line is JavaScript code.

### FILES
Filename |Purpose
:--------|:------
tagui|main runner for TagUI web automation
tagui.cmd|main runner for Windows platform
tagui.py|interface for Sikuli visual automation
tagui_config.txt|web browser settings used for automation
tagui_crontab|to run service request batch from crontab
tagui_footer.js|footer template for CasperJS code
tagui_header.js|header template for CasperJS code
tagui_parse.php|to interpret natural language into code
tagui_report.php|to generate html report from text log
tagui_runner.php|retrieving service requests from queue
tagui_service.php|receiving service requests into queue
tagui_service.in|log to track incoming service requests
tagui_service.out|log to track processed service requests
tagui_service.log|log to track service requests history
tagui_service.act|service request batch ready to execute
tagui_service.run|service request batch currently running
tagui_service.done|service request batch finished running
tagui_sikuli.in|interface in-file for Sikuli integration
tagui_sikuli.out|interface out-file for Sikuli integration

# Be a Force for Good
TagUI code is intentionally made honest and not hiding identity as an automated user

# License
TagUI is open-source software released under the MIT license
