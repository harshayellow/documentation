---
title: Call workflow
sidebar_label: Call workflow
---

A workflow is a predefined action or process your AI agent can trigger during a conversation. Use this option to execute tasks like retrieving booking details, processing payments, verifying user information, or updating records. You can pass user inputs as variables to the workflow and capture the output for use in later steps.

The table below describes the fields available in the Workflow action (How does the workflow work?):

| Step                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Trigger the workflow** | When the conversation reaches the Call workflow action, the AI agent activates the linked workflow.                                                                                                                                                                                                                                                                                                                         |
| **Pass input variables** | The AI agent sends relevant input data (e.g., booking ID, user name) collected earlier in the conversation to the workflow.                                                                                                                                                                                                                                                                                                 |
| **Workflow processing**  | The workflow executes its logic to perform tasks, automate backend operations, and handle complex scenarios, such as: <ul><li>Fetching data from APIs or databases (e.g., retrieving weather updates using location data)</li><li>Raising support tickets (e.g., for flight cancellations)</li><li>Connecting to a human agent when needed</li><li>Executing custom functions (e.g., calculating baggage charges)</li></ul> |
| **Store output**         | The workflow’s response (e.g., booking status, payment confirmation) is stored in a variable for use in subsequent conversation steps.                                                                                                                                                                                                                                                                                    
### Output node in Workflows

The Output node in a Workflow defines what data is returned once the workflow has finished executing. This data can be text, variables, or rich media, and it is passed back to the conversation that triggered the workflow. The returned output can then be used in the following steps of the conversation to deliver dynamic responses.

The Output node ensures that results from operations like API calls, database queries, or logic functions are returned in a structured usable form to the AI agent to continue the conversation based on real-time data.

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/outputnode1.png" alt="drawing" width="90%"/>

**Types of Output**

You can configure the Output node to return one of the following types:

1. **Static**: Returns a predefined text message when the Workflow completes.<br/> **Use case**: Use this when the output is static and does not depend on dynamic input.<br/> **Example**: "Thank you! Your request has been submitted."
2. **Variable**: Returns dynamic content stored in a variable, such as values fetched from APIs, databases, or functions.<br/> **Use case**: When the workflow depends on user inputs or dynamic data.<br/>  Store the weather temperature fetched from an API and use it later in the conversation.
3. **Rich media**: Returns visually enhanced responses for user engagement. Rich media is supported across web and messaging platforms like WhatsApp. Types of Rich media:
   * **Quick reply** – Displays button-based options for easy user input.
   
      ![Quick reply workflow](/files/quickreplyworkflow.gif)

   * **WhatsApp list** – Displays a structured list of selectable items.

      <gif></gif>

   * **Cards** – Display images, titles, and buttons in a visually engaging format.

      ![Carousel workflow](/files/carouselworkflow.gif)

### Output path

Use the Output path when you set the Output type to Variable. It lets the workflow return specific data from a larger API response.

When the workflow receives a complex or nested response (like JSON), you can extract only the needed data by using dot notation in the Output path field.

By using the Output path, you ensure the workflow sends only the relevant part of the response back to the conversation.

**How to use it**:

Suppose your API response looks like this:

```json
{
  "main": {
    "temp": 27.5,
    "humidity": 80
  },
  "weather": [
    {
      "description": "partly cloudy"
    }
  ]
}
```

You can use the Output path to extract:

**String**
* Temperature: `main.temp`
* Humidity: `main.humidity`

**Array**
* Weather description: `weather[0].description`

These paths will extract specific value from the response and assign it to your selected output variable to use in the next conversation step.

**Best practices:**

* Always preview the structure of your API before defining the path.
* Use an Output path when you want the particular value, not the full response.
* Use array notation ([0], [1]) for accessing items in lists or arrays.

### Create a workflow

To create a worflow, follow these steps:

1. Navigate to **Agents** > **Prompts** > **Actions** > **Call workflow**.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/callworkflow.png)
    
2. Click **+ Create workflow**.

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/createworkflow1.png" alt="drawing" width="40%"/>

3. Provide a **Workflow name** and **Description** to explain the purpose of the workflow.

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/workdetails.png" alt="drawing" width="50%"/>
   
4. This will create a new workflow where you can configure with the required input parameters, logic, and output settings.

* You can also create a workflow via the [Workflow builder section](https://docs.yellow.ai/docs/platform_concepts/studio/build/Flows/journeys#create-a-workflow-via-workflow-builder-section).

### Define a workflow

Defining a workflow allows the AI agent to perform automated backend tasks such as retrieving, validating, or storing data based on the user's input during a conversation. 

When defining a workflow, you need to use variables collected during the conversation (such as user name, travel date, or contact number) and pass them into the workflow. These variables drive the logic within the workflow and determine what actions are taken.

**A well-defined workflow helps you to:**

* Automate backend operations like API calls or database updates.
* Use dynamic inputs from the user by mapping variables into the workflow.
* Maintain consistency and reduce duplication across conversation flows.

**Use case**: Fetch and store user booking details

To define a workflow, follow these steps:

1. Use prompts to collect user details for flight booking and store them in input variables.

      <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/database.png" alt="drawing" width="80%"/>
      
2. [Create a database](https://docs.yellow.ai/docs/platform_concepts/studio/database#create-database-table) with columns matching the fields you want to store (example, name, phone number, destination).

   ![](https://cdn.yellowmessenger.com/assets/yellow-docs/db.png)

3. Go to the workflow that you have created and add a Database node and select the created database. For more information, click [here](https://docs.yellow.ai/docs/platform_concepts/studio/database#insert-new-records-or-values-into-a-database-table).

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/dbserach.png" alt="drawing" width="80%"/>
   
4. Click **Define** and map the input variables to the corresponding database columns.

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/definewrok.png" alt="drawing" width="50%"/>
   
5. Link the Database node to the Output node to complete the workflow.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/output.png" alt="drawing" width="80%"/>
  
### Call a workflow in prompt

Once you have defined a workflow, you need to call it from a prompt to trigger it during a conversation. This allows the AI agent to perform backend operations such as fetching or storing data based on user input collected earlier in the conversation.

This connects the user’s interaction to backend logic in real-time to enable actions such as database updates, API calls, or data validation.

**Use cases**

Here are some examples of how workflows can be triggered via prompts:
* **Database**: Store a user’s booking details (example, name, phone, destination).
* **API integration**: Fetch real-time flight status or weather updates.
* **Validation**: Confirm if an entered email is already registered.
* **Service ticket**: Submit a refund or cancellation request and get a reference ID.

Let us consider the below use case:

**Use case:** Book a flight and store booking details

A user provides travel information (example, name, destination, travel date). The AI agent collects this data through prompts and then calls a predefined workflow to store the information in a database.

**How to call a workflow in a prompt?**

To call a workflow in a prompt, follow these steps:

1. Navigate to **Agents** > **Prompts**, and go to the prompt where the workflow should be triggered.

2. Click **Action** and select **Call workflow**, or use the shortcut key `$`.

   ![](https://cdn.yellowmessenger.com/assets/yellow-docs/callworkflow.png)

3. Choose the workflow you previously created from the drop-down. 

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/traveldb.png" alt="drawing" width="80%"/>
  

4. Click the **Edit** icon next to the selected workflow and map the required input variables (example, user_name, travel_date) that were collected during the conversation.

   ![](https://cdn.yellowmessenger.com/assets/yellow-docs/mapworkflow.png)

5. Click **Save** to complete the configuration.

* Once configured, the workflow will automatically be triggered when the conversation reaches this prompt. The workflow’s output can be stored in a variable and used in the next steps of the conversation.


### Use case: Fetch weather updates using API via workflow

This use case demonstrates how the AI agent can retrieve and display real-time weather updates based on user-provided location inputs using a backend API workflow.

#### Step 1: Define the Workflow

You need to create a backend workflow that accepts location inputs, calls a weather API, and returns the temperature and weather conditions.


1. Navigate to **Agents** > **Prompts** > **Actions** > **Call workflow** and click **+ Create workflow**. (name workflow GetWeatherUpdate).

     ![](https://cdn.yellowmessenger.com/assets/yellow-docs/callworkflow.png)

2. Use a Variable node at the start of the workflow to define the input parameters needed for the API. For this use case, define: **latitude** and** longitude**.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/variableskill.png)

3. [Add a API node](https://docs.yellow.ai/docs/platform_concepts/studio/api/add-api-apinode#import-api) to import a weather API and configure it with the following details:
    * **API**: Select the API that you have added.
    * **Name**: Enter the name of the API.
    * **Method**:  Enter the method as GET.
    * **URL**: Enter the URL as `https://api.openweathermap.org/data/2.5/weather?lat=12.9716&lon=77.5946&appid=fab8b859cea632996b45a82f2361b345&units=metric`

     <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/APInode.png" alt="drawing" width="80%"/>

4. Store the full API response in a variable.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/storeresponse.png)

5. Define the workflow by mapping the specific fields that you want to use from the API response, like latitude, longitude, or humidity.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/apimap.png)

6. Add an Output node to return the mapped values and set:<br/>

    i. **Type of output**: Choose **Variable** as the output type.<br/>
    ii. **Select a variable**: Select a variable storing the API response.<br/>
    iii. **Path**: Use dot notation (example, main.temp) to extract specific values from the API response. 

* This set up completes the workflow definition. You can now use the workflow in the conversation.

#### Step 2: Call workflow in prompt

Once the workflow is defined, connect it to your conversation using the **Call workflow** action in  the prompt section.

1. Write a prompt that asks the user for their location. Example: "Please share your location or enter latitude and longitude". 

2. **Call workflow** action in the prompt and choose the GetWeatherUpdate workflow from the list.

      ![](https://cdn.yellowmessenger.com/assets/yellow-docs/callworkflowpro.png)

3. Click the **Edit** icon and map the collected latitude and longitude to the workflow inputs and assign the output from the workflow to a variable.

   ![](https://cdn.yellowmessenger.com/assets/yellow-docs/loading.png)

4. Click **Save** to complete the configuration.
    
Refer to the following GIF to see the complete process of fetching weather updates using an API via a workflow:

   ![Weather API skill](/files/weatherAPIskill.gif)