# Streamlining IT Support Operations with Autonomous Copilot Agent using Copilot Studio

**Estimate Time: 60 mins**

## Objective

The objective of this lab is to enable participants to streamline IT
support operations at Contoso Solutions by creating an autonomous
Copilot agent. Participants will learn to set up Microsoft Copilot
Studio, configure the IT Support Agent, integrate Power Apps and
Dataverse, enhance the bot’s capabilities with a knowledge base, and
automate ticket creation using Power Automate. This hands-on lab will
equip users with the skills to improve IT workflows, reduce manual
effort, and enhance support efficiency.

## Solution

Participants will create a customized Contoso IT Support Agent using
Microsoft Copilot Studio, configure it to handle common IT issues, and
integrate it with Dataverse for storing support data. They will set up a
development environment, add knowledge sources, and refine the bot's
conversation flows for better user interaction. By leveraging Power
Apps, participants will create a Dataverse table to manage IT support
records. Using Power Automate, they will automate ticket creation and
email notifications for unresolved issues. Finally, participants will
test the agent to validate its troubleshooting accuracy and workflow
automation, ensuring seamless IT support operations.

# Exercise 1: Getting Started with Power Apps

This exercise introduces participants to Power Apps and Dataverse. The
goal is to log in to Power Apps, set up a working environment, and
create a Dataverse table by importing data from an Excel file.
Participants will learn essential skills for working with data-driven
applications.

## Task 1: Logging into Power Apps

1.  Navigate to power apps website +++https://www.microsoft.com/en-us/power-platform/products/power-apps+++ and click on the **Try for Free** button.

    ![](./media/image15.png)


2.  Enter the **Administrative Username** from the **Office 365 Tenant** section of the **Resources** tab into the email field, **select** the **checkbox** and click on the **Start free** button.
    
    ![](./media/Picture4.png)

3.	Enter the **Administrative Password** and you will be taken to the Power Apps Home page.
   
4.	Select **Yes** in the Stay Signed in dialog and **Got it** for the Save password prompt and select **No, Thanks** in the Sign in to Microsoft Edge pop up.

    >[!Note] **Note:** If it agains prompts for the user name, password or any information to login, please provide the same and login.
   
## Task 2: Setting Up a Dataverse Table

1.  Ensure that the **Dev One** environment is selected. Select it if not done already.

    ![](./media/img1.png)

2.  From the left navigation bar select **Tables.** In the tables
    section top bar click on the **+ New table** and then select
    **Create new tables**.

    ![](./media/image21.png)


3.  Select **Import an Excel file or CSV** option to create a new table.

    ![](./media/image22.png)


4.  Click on the **Select form device** option and select **Support Ticket**
    excel file from **C:\LabFiles** folder.

    ![](./media/image23.png)


5.  Select the table and click on **View data** to see the table.

    >[!Note] **Note:** In this case, the table is named *Employee Technical Support Record*. The name may vary with each execution. Please save the table name for future reference. The column name may also vary in the execution.

    ![](./media/image24.png)


6.  Go to table data, select the drop down next to the **Technical Issue Description** field,
    select **Edit column**, Set the data type as **Text** 🡪 **Multiple
    line** 🡪 **Plain Text** and click on the **Update**. The column name
    may be different in each case.

    >[!Note] **Note:** The **column name might be slightly different**, but it will be something similar to the issue description since it is Copilot generated.

    ![](./media/image25.png)


    ![](./media/image26.png)


8.  Select drop down next to the **Current Status** field, select **Edit column**, Set
    the Choices as +++**Unresolved**+++, +++**Resolved**+++, +++**Processing**+++. Set Default
    choice as **Unresolved** and click on the **Update**.

    ![](./media/image27.png)


9.  From top right side click on **Save and exit** to save the table.

    ![](./media/image28.png)


## Conclusion

By completing this exercise, participants will learn:

- How to access and navigate Power Apps using office 365 admin tenant credentials.

- Steps to create and configure a Dataverse table by importing data.

- Practical knowledge of setting up an environment to support app
  development workflows.

#  Exercise 2: Creating the Contoso IT Support Agent

This exercise focuses on logging into Microsoft Copilot Studio and
creating a customized Copilot agent tailored for IT support operations
at Contoso. Participants will gain hands-on experience navigating
Copilot Studio, configuring environments, and building an AI-powered
agent to streamline IT workflows.

## Task 1: Logging into Microsoft Copilot Studio

1.	Navigate to the url +++https://copilotstudio.microsoft.com+++ and click on Start free trial to start the Copilot Studio trial.

    ![](./media/image100.png)

##  Task 2: Creating and Configuring Contoso IT Support Agent 

1.  In Copilot Studio home section from top right, select the **environment** and choose **DevOne** environment. 

    ![](./media/image6.png)


2.  On welcome copilot studio tab, click on the **Skip** to move
    forward.

    ![](./media/image7.png)


3.  From left navigation bar select **Create** and then select **New agent** to start creating new agent.

    ![](./media/image8.png)


4.  From top right corner click on **Skip to configure** button.

    ![](./media/image9.png)


5.  Enter **Name, Description and Instruction** of the agent as given
    below and click on **Create** button.

    **Name:** +++Contoso IT Support Agent+++
    
    **Description:** +++Create a Contoso IT Support Agent which transforms IT support at Contoso Solutions by providing instant troubleshooting for common issues, automating ticket creation for unresolved problems, and storing all interactions in Dataverse. This solution enhances response times, reduces manual workloads, and boosts employee productivity.+++
    
    **Instruction:** +++Create the Copilot Agent and configure it to handle IT support operations. Add a knowledge source containing solutions for common IT issues like hardware troubleshooting, connectivity, and software glitches. Set up a trigger to detect incoming emails from employees describing unresolved issues. Create an action to save these technical issues into a Dataverse table, ensuring all details are stored for tracking and reporting. Test the agent to validate its troubleshooting accuracy and ticket automation workflow before deployment.+++

    ![](./media/image10.png)


6.  On the overview page of Contoso IT Support Agent, **Enable** the
    orchestrator for the agent.

    ![](./media/image11.png)


7.  On the overview page of the agent, **Disable** the “**Allow the AI to
    use its own general knowledge**” option.

    ![](./media/image12.png)


8.  From top right corner of the agent, click on the **Settings**
    button.

    ![](./media/image13.png)


9.	Then go to **Generative AI** section, select **Generative**, set content moderation as **Medium** and click on **Save** to save the setting.

    ![](./media/image101.png)


##  Conclusion

By completing this exercise, participants will learn:

- How to access and set up Microsoft Copilot Studio.

- Steps to create and configure a custom Copilot agent.

- Practical skills in enabling generative AI and orchestrator settings
  for the agent.

- Ways to enhance IT operations by automating ticket creation and
  leveraging AI for troubleshooting.

# Exercise 3: Enhancing Bot Capabilities

This exercise focuses on enhancing the capabilities of the Contoso IT
Support Agent by adding a knowledge base and customizing bot topics for
improved interaction. Participants will refine the bot's responses and
ensure it effectively assists users in troubleshooting and escalation.

## Task 1: Add Knowledge Base 

1.  On the Contoso agent overview page, scroll down and click on **+ Add
    Knowledge** button.

    ![](./media/image29.png)


2.  Select **Click to browse** button to add the lab file **Contoso Common IT Issue.docx** from **C:\LabFiles** folder and then click on **Add** to save the file.

    ![](./media/image30.png)


    ![](./media/image31.png)

3.  Again, go to agent overview page, scroll down and click on **+ Add knowledge.**

    ![](./media/image32.png)


4.  Select **Dataverse (preview)** option as data source.

    ![](./media/image33.png)


5.  In top right corner search bar, enter and search for +++**Employee**+++
    and select **Employee Technical Support Record** table. Then click
    on the **Next, Next** and **Add** button to add the knowledge
    source.

    **Note:** The **table name might be different** in your case since it is a Copilot generated one.
    
    ![](./media/image34.png)


    ![](./media/image35.png)

    >[!Alert] **Important:** From the Knowledge page, ensure that the added knowledge source has been successfully uploaded. This will generally take 10 to 15 minutes to complete.

## Task 2: Customize the Conversation Start Topic

1.  From the top bar option click on **Topics** and then click and open
    **Conversation Start** topic.

    ![](./media/image36.png)


2.  Scroll down and go to message node. Update the message after bot
    name as given below:

    Hello. I’m Bot Name, a virtual assistant. +++How can I help you?+++

    ![](./media/image37.png)


3.  From top click on the **Save** to save the topic.

    ![](./media/image38.png)


##  Task 3: Update the Fallback Topic 

1.  From the top bar option click on **Topics** and then open the
    **Fallback** topic.

    ![](./media/image39.png)


2.  Scroll down and go to message node. Update the message as given
    below:

    +++I’m sorry. This information is not available in my system. You can raise the support ticket via mail for this issue.+++

    ![](./media/image40.png)


3.  From top right side click on the **Save** button to save the topic.

    ![](./media/image41.png)


##  Conclusion

By completing this exercise, participants will learn:

- How to upload and integrate a knowledge base to enhance the bot's
  functionality.

- Steps to customize conversation start messages for a more engaging
  user experience.

- Techniques to update fallback responses for better handling of
  unsupported queries.

# Exercise 4: Test the agent

This exercise guides participants through testing the Contoso IT Support
Agent to validate its functionality. Participants will check how the bot
handles prompts using the knowledge base and fallback topics to ensure
seamless interaction and escalation.

1.  From top right corner click on the **Test** button. Then in test
    section click on **Map** turn it **On** and then click **Refresh**.

    ![](./media/image42.png)


2.  Enter the prompt +++**My printer is not working how to fix it**+++ . It gives the solution as per knowledge source.
    
    ![](./media/image43.png)


3.  Again, give the prompt +++**Two factor Authentication (2FA) issue**+++ .

    ![](./media/image44.png)


4.  The 2FA issue and solution is not available in the knowledge source
    so it will go to fallback topic and return prompt related to Raise
    Ticket.

    ![](./media/image45.png)


## Conclusion

By completing this exercise, participants will learn:

- How to test and activate an AI agent for troubleshooting.

- Validation of the bot’s ability to respond using its knowledge base.

- How fallback topics handle unsupported queries and redirect users
  effectively.

# Exercise 5: Automating Support Ticket Creation with Power Automate

This exercise demonstrates how to automate support ticket creation using
Power Automate and integrate it with the Contoso IT Support Agent.
Participants will create a flow to streamline issue reporting, record
data in Dataverse, and notify support engineers via email.

1.  Go to overview page of the agent, scroll down and click on **+ Add action**.

    ![](./media/image46.png)


2.  In choose an action window, From top left side click on the **+ New Action** and select **New Power Automate Flow** . 

    ![](./media/SS1.png)


3.  In Power automate flow, click on **When an agent calls the flow** and then select **Add an Input**.

    ![](./media/SS2.png)

    ![](./media/SS3.png)


5.  Select **Text** as data type of input and rename the input as +++**Name**+++.

    ![](./media/SS4.png)


    ![](./media/SS5.png)


6.  With same procedure create more input as per given below details.

    | **Input Name** | **Data Type** |
    |----------------|---------------|
    | +++ID+++             | Text          |
    | +++Email+++          | Text          |
    | +++Details+++        | Text          |
    
    ![](./media/SS6.png)


7.  Below **When an agent calls the flow**, click on **(+)** sign and select **Add an action**.

    ![](./media/SS7.png)


8.  In Add an action search bar, enter +++**Add a new row**+++ . Then select
    **Add a new row** from Microsoft Dataverse section.

    ![](./media/SS8.png)


    > Note: Sometimes, a Dataverse connection is not created automatically. You may need 
to **sign in** again with your credentials **OAuth** authentication.
    
    ![](./media/SS9.png)


9.  In **Table Name** section search and select +++**Employee Technical Support Record**+++ (or your corresponding table name created).

    ![](./media/SS10.png)


10.  Below table name select **Show all**, then click on the particular
    field and add input with the help of dynamic content button (Thunder
    bolt) as per the below table. The **Current Status** field
    should be selected with drop down as **Unresolved**.

    | Section                     | Input Variable          |
    |-----------------------------|-------------------------|
    | Employee Name               | Name (Dynamic Input)    |
    | Email Address               | Email (Dynamic Input)   |
    | Employee ID                 | ID (Dynamic Input)      |
    | Technical Issue Description | Details (Dynamic Input) |

    ![](./media/image56.png)
    
    
    ![](./media/SS11.png)


11. Below Add a new row action click on (+) and select **Add an action**.

    ![](./media/SS12.png)


12. In add an action section, enter +++**Send an email**+++ in the search bar
    and select **send an email (V2)** from office 365 outlook section.

    ![](./media/SS13.png)

    ![](./media/SS14.png)


14. In send an email section, Enter the below given detail in the
    respected section:

    Replace the place holders for **Name**, **ID**, **Details** with the variables using dynamic content
    
    **To**
    
    
    Enter support engineer email (**Use any email ID** - It will be to this id, the mail will be sent by the agent to when Support Ticket is raised) 


    **Subject**
    
    ```
    New Technical Support Ticket Raised 
    ```

    **Body**

    ```
    A new technical support ticket has been raised and requires your attention. Please find details below:
    
    Employee Name: < Name >
    Employee ID: < ID > 
    Technical Issue: < Details >
    
    Thank you for your prompt attention to this matter.'
    
    Best Regards
    ```


    ![](./media/SS15.png)


15. From top left corner rename the flow as +++**Create an Employee Support Ticket**+++.

    ![](./media/SS16.png)


16. From top bar click on **Save draft** and then click **Publish**. **Close** the Power automate tab.

    ![](./media/image62.png)


17. Go back to Copilot window and click on **Refresh** button.

    ![](./media/image63a.png)


18. In Choose an action window, select **Create an Employee Support Ticket** flow.

    ![](./media/SS17.png)


19. Click on **Add action** button to add a flow.

    ![](./media/SS18.png)


20.	From the **Overview** page of the agent, under the **Action** section, select **Edit** to Edit the parameters of the action. Select the **Inputs** section.

    ![](./media/SS19.png)
    
    ![](./media/SS20.png)


21. Enter the given description in the respected input field, after entering
    the description click on **Save** button. 

    | Section | Details |
    |----|----|
    | Name -- Description | +++Enter the name of the employee.+++ |
    | ID -- Description | +++Enter the employee ID in the field.+++ |
    | Email -- Description | +++Enter the email address of the employee from whom the email is received.+++ |
    | Details -- Description | +++Enter the email details of the employee.+++ |

    ![](./media/img7.png)
    
    ![](./media/img8.png)





## Conclusion

By completing this exercise, participants will learn:

- How to integrate Power Automate flows with a Copilot agent for ticket
  creation.

- Steps to collect and map input data dynamically from user
  interactions.

- Techniques to automate email notifications for technical issue
  escalation.

- The ability to configure workflows for efficient support ticket
  management.

# Exercise 6: Configuring an Email-Based Trigger for Automated Actions

This continuation of automating support ticket creation focuses on
setting up a trigger in the Contoso IT Support Agent to link email
inputs with the automated Power Automate flow. Participants will
configure triggers and finalize the agent for deployment.

1.  Go to overview page of the agent, scroll down and click on **+ Add trigger**.

    ![](./media/SS21.png)


2.  Then from Add trigger window, select **When a new email arrives (V3)** trigger.

    ![](./media/image71.png)


3.  After successful connection of copilot and outlook and green tick appears click on **Next** button.

    ![](./media/image72.png)


4.  In folder field select folder icon and select **Inbox** folder and then select **Create trigger**. 

    ![](./media/image73.png)


    ![](./media/image74.png)


5.  Close the **Time to test your trigger** prompt. On Support agent overview page scroll down, on trigger section click on three dots **(…)** and select **Edit in Power Automate.**

    ![](./media/SS22.png)


6.  Right click on When a new email arrives trigger and select **Delete**.

    ![](./media/image76.png)


7.  Then click on Add a trigger, search for +++**When new email arrives**+++
    and select **When a new email arrives** trigger from **Office 365
    outlook** section.

    ![](./media/image77.png)


8.  Click on **Send a prompt to the specified copilot for processing**,
    in body/message section enter the prompt, +++**Run Create an Employee Support Ticket flow and use content from Body From.**+++ Replace **Body** and **From** as dynamic content variable.

    ![](./media/img9.png)


9.  **Save** and **Publish** the flow, close power automate window and
    go back to copilot window.

    ![](./media/image79.png)


10. Go to overview section and from top right corner click on
    **Publish** and again click **Publish** to publish the copilot.

    ![](./media/image80.png)


    ![](./media/image81.png)


## Conclusion

By completing this exercise, participants will learn:

- How to set up triggers in Copilot to automate workflows based on email
  inputs.

- Steps to dynamically map email content to Power Automate flows.

- The process of publishing and finalizing the AI agent for operational
  use.

- Practical skills in linking communication tools like Outlook with
  automated workflows.

# Exercise 7: Test the agent

This exercise focuses on testing the integration of the Contoso IT
Support Agent with Power Automate and Outlook. Participants will verify
the agent's ability to process emails, create support tickets, and
trigger automated workflows effectively.

1.  Go to overview page of agent, scroll down, click on **(…)** on
    trigger and select **Edit in power automate**.

    ![](./media/image82.png)


2.  It will navigate to power automate flow, from top bar click on
    **Test** button and then select **Manually** and again click on
    **Test**.

    ![](./media/image83.png)


    ![](./media/image84.png)


3.	**Send an email** to the 365 admin tenant mail id from any other mail box in order to **trigger the action**. The mail should be describing an issue and should have your details like employee id in it, similar to the one in the below screenshot. Example content is as below

    ```
    Hi Support Team,
    
    I hope this message finds you well.
    Iam Mark Brown, working as a Software Engineer at Contoso. My employee ID is CONTOSO099
    Issue: Monitor is completely balank and not functioning.
    Kindly raise a support ticket and assist in resolving this issue at the earlierst.
    Thank you for your support.

    Best Regards,
    Mark Brown
    ```
    
    ![](./media/image85.png)

    ![](./media/image86.png)

4.  Navigate to copilot agent overview page, scroll down and select
    **Test trigger**.

    ![](./media/SS23.png)


5.  Click on **Start testing**, it will start testing.

    ![](./media/image88.png)


6.  In test section click on the **Connect**, it will open the
    connection window.

    ![](./media/image89a.png)


7.  Click on the **Connect** again and then select **Submit.**

    ![](./media/image90.png)


    ![](./media/image91.png)


8.  Navigate to copilot studio window and re run the **Test**.

    ![](./media/SS24.png)


9.  The support request is automatically generated.

    ![](./media/image93a.png)


10. Navigate to power apps and go to Employee support ticket record
    table, and check the details.

    ![](./media/image94.png)


11. Check the Support mail which we configure in power automate flow to
    send an email. The email is automatically sent to the support team.

    ![](./media/image95.png)


12. Go to test window and writer query as user +++**Mark Brown Ticket Current Status**+++ . It gives the status of the issue as unresolved.

    ![](./media/image96.png)


13. As Support Engineer, write a prompt in the test section. +++**I want to know about all Unresolved ticket**+++ .

    ![](./media/image97.png)


## Conclusion

By completing this exercise, participants will learn:

- How to test the agent's functionality by simulating real-world
  scenarios.

- Steps to validate email-triggered workflows and ticket generation in
  Power Automate.

- How to review generated records in Dataverse and ensure notifications
  are sent to the support team.

- Practical insights into debugging and finalizing automation workflows.

# Final Conclusion of the Lab Guide

This lab guide provided participants with a hands-on experience in
deploying an Autonomous Copilot Agent for Contoso Solutions' IT support
service desk. By following the step-by-step exercises, participants were
able to:

1.  **Set Up Copilot Studio**: Participants learned how to log into
    Copilot Studio, create and configure the IT support agent, and
    enable essential settings like generative AI and orchestrator for
    effective troubleshooting and ticket automation.

2.  **Navigate Power Apps**: Participants gained practical knowledge in
    logging into Power Apps, setting up a Dataverse table, and importing
    data from Excel to track and manage support tickets efficiently.

3.  **Enhance Bot Capabilities**: The exercises focused on adding a
    knowledge base to the bot, customizing the conversation start and
    fallback topics to improve user interaction, and ensuring the bot
    could handle a wide range of IT support scenarios.

4.  **Automate IT Support Tasks**: Participants also learned how to
    automate the creation of support tickets using Power Automate,
    enhancing the bot's capability to manage unresolved issues and
    improve IT team workflows.

By completing these exercises, participants were able to implement a
robust autonomous support system that improves response times, reduces
manual workload, and enhances overall productivity for IT support
operations. The integration of Copilot Studio, Power Apps, and Dataverse
ensures a seamless flow of information, automates routine tasks, and
optimizes support workflows, providing immediate troubleshooting
solutions to employees and automated ticket management for unresolved
issues.
