---
title: Get input
sidebar_label: Get input  
---

Use **Get input** to collect and store user responses in variables, this allows the AI agent to reuse the data in future interactions. It ensures that inputs are validated before storing the input.

For example, if a user provides their name, the bot can use it in future intercations.

**Types of inputs**

When creating an input, different input types can be selected based on the use case:

* **[Name](#get-name-input)** – Captures the user’s name.
* **[Email](#email)** – Collects the user’s email address.
* **[Phone](#phone)** – Gets the user’s phone number.
* **[Quick reply](#add-quick-reply-buttons-to-the-ai-agent)** – Provides users with predefined response options.
* **[Carousel](#carousel)** – Displays multiple options in a scrollable format.
* **[Date](#date)** – Allows users to select or input a date.
* **[Custom](#custom)** – Enables a more flexible input type tailored to specific needs.
* **[Location](#location)** - Captures the user’s location based on the user input.
* **[Dynamic rich media](#dynamic-rich-media)** - Displays interactive options like cards with images and action buttons that are generated dynamically.
* **[Feedback](#get-feedback-input)** - Collects the user's feedback.

### Create input

To create a input, follow these steps:

1. Go to **Agents** > **Prompt** > click on **Actions** > **Get input**.

  ![image](https://cdn.yellowmessenger.com/assets/yellow-docs/get-ipnut.png)

2. Click **+ Create input**.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/create-input1.png" alt="drawing" width="40%"/>


3. Select your preferred input type based on the use case.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/choose-inputtype.png" alt="drawing" width="50%"/>


### Get name input

Use **Get name input** to capture and store the user's name during a conversation. This input remains available throughout the session and can be reused by referencing the same input name in the other conversations.

The table below describes the fields available in the Get Name Input action:

Field name | Description
-----------|------------
Input Name (Mandatory) | Defines the name of the input field where the user’s response will be stored. In this case, the field is labeled as **Name**.
Data type | Default data type is displayed. In this case, it is a String, meaning it only accepts text values.
Description | Provide additional details or context about the input field. This helps define how the AI agent will use the captured input.
Validation | Enter the validation rules to ensure the user provides valid input.<br/> Examples: – Allow upto 50 characters.<br/>– Reject names containing numbers.
Others | Enable **Mark User Input as Optional** checkbox:<br/> * If checked, the user is not required to provide their name.<br/> * If unchecked, the bot will prompt the user until a valid name is provided.

![Get input name](/files/name-input.gif)

### Email

Use Get Email input to collect and store a user’s email address during a conversation.

The table below describes the fields available in the Get Email input action:

Field name | Description
-----------|------------
Input name (Mandatory)| Specifies the name of the variable where the user’s input will be stored.
Data type |	Default data type is displayed. For email input, it is set as String.
Description (Mandatory) | Provide context about the input field. Example: "Collect user email ID" to inform the AI agent about the purpose of this input.
Validation | Ensures the user input follows the correct format. The current validation rule requires the email to contain exactly one "@" symbol to be considered valid. Additional validation rules can be added.
Example of User Input |	Provide an example of a valid email address, such as "johndoe@gmail.com", to guide users in entering the correct format.
Others | Enable **Mark user input as optional** checkbox:<br/>*	If checked, users are not required to provide an email address.<br/>* If unchecked, the bot will prompt the user until they enter a valid email.

![Email input](/files/email_input.gif)


### Phone

Use the **Get Phone input** action to collect and store a user’s phone number during a conversation. The collected number is saved in a variable and can be used for tasks such as sending notifications, verifying the user’s identity, or linking to order details.

The table below describes the fields available in the Get Phone Input action:

Field name | Description
-----------|------------
Variable name (Mandatory) | Define the variable where the user’s phone number will be stored. Example: mobile_Number.
Data type | Specify the type of data expected from the user. For phone input, it is set as Number.
Description	| Allows the user to provide additional details about the purpose of collecting the phone number. This field helps define how the AI agent will use the input.
Examples of expected input | Provides sample responses to help users understand the expected input format. Example: +91 9876543210.
Validation | Ensures the user input follows the correct format. In this case, users must select a country code to ensure proper phone number formatting. Additional validation rules can be added if needed.
Always save number with country code | If this option is enabled, the system will store the phone number with a country code, even if the user does not provide it.
Mark user input as optional | If checked, the user is not required to provide their phone number. If unchecked, the bot will prompt the user until a valid phone number is provided.

![Phone input](/files/phone-input.gif)

### Add Quick reply buttons to the AI agent

Use quick replies to present users with tap-to-select response options. They simplify input, reduce typing effort, and keep conversations on track.



The table below describes the available configuration fields:

Field name | Description
-----------|------------
Input name | Specifies the name of the input field where the selected quick reply will be stored.
Data type | Default data type is displayed. For quick reply input, it is set as String.
Description | Provide additional context or instructions about the quick reply input.
Dynamic options | Toggle this option to generate quick reply choices dynamically using variables. 
Options | Click **+ Add** to create static quick reply choices for users. More options can be added as required.
Others | Enable **Allow users to type input manually** (Checkbox) to protect sensitive information by replacing the characters with symbols to maintain privacy.

Refer to the following GIF to see how the Quick reply input will work:

![Quick reply](/files/quickreply.gif)

### Carousel

Use a carousel to present multiple options as horizontally scrollable cards. Each card can contain an image, title, description, and one or more buttons for user actions.


The table below describes each field in the carousel configuration:

Field name | Description
-----------|------------
Input name | The variable name where the selected response from the carousel will be stored.
Data type |	Default data type is displayed. For carousel input, it is set as String.
Description	| Enter a brief explanation of the input's purpose to provide clarity on what information is being collected.
Dynamic response | Toggle this option to generate carousel options dynamically using variables instead of static data.
Cards |	The individual items displayed in the carousel, which can include images, text, and buttons.<br/> **Image**: Allows you to upload an image (less than 10MB) to display the visual representation of the carousel item.<br/> **Title**: The main heading for the carousel item, giving a quick overview of the option.<br/> **Description**: Additional details about the carousel item to provide context to users.<br/> **Buttons**: Click **+ Add** button to add interactive buttons for each carousel item, enabling actions such as selecting an option or opening a link.
Others | Enable **Allow users to type input manually** (Checkbox) to enable users to type a response instead of selecting a button in the card.
 <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/staticcarousel.png" alt="drawing" width="60%"/>
 <br/>

 
### Date

Use the date input field to collect structured, date-specific responses from users. You can apply validation to ensure the input falls within a defined range or meets formatting requirements.


The table below describes each field in the date configuration:

Field name | Description
-----------|------------
Input name	| Enter the name where the user's selected date will be stored.
Data type |	Default data type is displayed. For date input, it is set as "Date".
Description | A brief explanation of the purpose of the date input field.
Validation | Ensures that the entered date meets specified constraints.<br/> **Range: Min. / Max:**	Allows setting a minimum and maximum date range to restrict user input within a valid timeframe.<br/> **Custom instructions**: Specifies the format in which the date should be entered or displayed (example, YYYY-MM-DD, MM/DD/YYYY).
Others | Enable **Mark user input as optional** to allow users to skip providing a date if they prefer not to share it.

![Date input](/files/dateinput.gif)

### Custom

Use a custom field to collect user input in a specific format, apply validation rules, and store the response in a variable for later use. This field is ideal for capturing data like order IDs, ZIP codes, or any other input requiring tailored validation.



The table below describes each field in the custom input configuration:

Field name | Description
-----------|------------
Input name | Enter the name of the custom variable where the user's input will be stored. This variable can be used in the conversation.
Data type |	Select the preferred data type based on the custom input such as String or Number.
Description | Enter a brief explanation of what the field is used for.
Example of user input | Provides a sample input to guide the user toward the correct format. For example: “CUST1234” for a customer ID.
Validation | Ensures that the user input follows specific rules or formats.<br/> **Add custom validation**: You can define specific rules that the user’s input must follow. This ensures that the AI agent collects accurate and correctly formatted data based on your business requirements.
Others | Use the **Mark user input as optional** checkbox to allow users to skip this question if they prefer not to provide the information.

![Custom input](/files/custominput.gif)

### Location

Use the **Get Location input** action to collect and store a user’s location during a conversation. The collected location is stored as an object variable and can be used for tasks such as coordinating delivery services, suggesting nearby options, or validating service availability based on the user’s area.

The table below describes the fields available in the Location action:

Field name | Description
-----------|------------
Variable name (Mandatory) | Define the variable where the user’s location will be stored. Example: user_Location.
Data type | Default data type is displayed. For quick reply input, it is set as Object.
Description	| Allows the user to provide additional details about the purpose of collecting the Location. Example: "Please share your current address for delivery".
Select allowed countries | Allows you to restrict the location input to specific country codes. Useful when services are limited to certain regions.
Add custom instruction | Optionally add more specific instructions or hints to guide the user in providing their location.
Mark user input as optional	| If this option is selected, the user is not required to provide their location. If unchecked, the agent will prompt the user until valid location data is shared.

  <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/locationinoput.png" alt="drawing" width="60%"/>
  
-----  

### Dynamic rich media

Dynamic rich media is used to display interactive, visually rich options to users such as carousels or cards that are generated dynamically. These responses are fetched via APIs or from functions via workflow.

You can use Dynamic rich media when:

* You want to personalize the experience with updated, real-time data.
* The options are not static and need to change based on API responses.
* You want to display content in a more engaging and structured format, such as a carousel or card layout.

**Examples**:

It is useful in scenarios where user options need to be customized for example:

* Displaying a list of available resorts or hotels
* Showing product recommendations
* Listing support ticket summaries
* Offering multilingual responses based on user preferences

**Supported Dynamic rich media:**

* Quick replies
* WhatsApp List
* Cards
* File
* Image
* Video
* Whatsapp carousel


The table below describes the fields available in the Dynamic rich media action:

Field name | Description
-----------|------------
Input name (Mandatory) | Define the name of the input field where the user’s response will be stored. 
Data type | Default data type is displayed. In this case, it is a String, meaning it only accepts text values.
Description | Provide details of what this input is about.
Linked workflow | Select the workflow you created to fetch and format the data.

#### How to configure Dynamic rich media

To configure and display dynamic rich media in your AI agent conversation, follow these steps:

   
<!-- 2. Add an [API node](https://docs.yellow.ai/docs/platform_concepts/studio/api/add-api) to fetch images and store the response in a variable of type object.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/getAPI-image.png)
    
3. Add a [Function node](https://docs.yellow.ai/docs/platform_concepts/studio/build/nodes/action-nodes-overview/function-node) to extract the image URL and name, and format them for display. Store the response in a variable.

     ![](https://cdn.yellowmessenger.com/assets/yellow-docs/image-function.png)
     
4. Add an **Output node**, select **Return a value**, and choose the variable where the response is stored.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/format-image.png)
    
    
#### Step 2: Call Workflow in Prompt section

1. In prompt section, trigger the Workflow to fetch the images.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/call-workflow-prompt.png)
    
#### Step 3: Use Dynamic rich media to display -->


1. Go to **Prompts** section  and click **Actions** > **Get input**.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/create-input.png)
     
2. Select **Dynamic rich media** action.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/dynamic.png" alt="drawing" width="50%"/>

3. Define the following fields:

    i. **Input name**: Enter the Input name.

    ii. **Describe what this input is about:** Provide details of what this input is about.
    
    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/dynamic-resort-fetch.png" alt="drawing" width="50%"/>

4. Click **Configure**.  

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/configure_workflow.png" alt="drawing" width="60%"/>

5.  Click **Insert**.   

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/insert1.png" alt="drawing" width="50%"/>

6. Click **Save**.    
    
7. Click **Edit** icon of the **Get input action**.

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/edit-dymanic-image.png" alt="drawing" width="70%"/>

8. Click **View details**.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/view-details.png" alt="drawing" width="50%"/>

9. Click **Define workflow** to configure the workflow output.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/define-workflow-1.png" alt="drawing" width="50%"/>

10. Add an **Output node**, select **Image**, and copy the sample variable format to display the dynamic image.  

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/dynamic-image-format.png" alt="drawing" width="70%"/>

11. Click on the drop-down and select **+ Create new variable**.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/create-new-variable.png" alt="drawing" width="50%"/>

12. Enter the variable details:

      i. **Variable name**: Specify the variable name.<br/>
      ii. **Data type**: Select the data type as object.<br/>
      iii. **Default value**: Paste the copied sample format or enter the image URL to display the dynamic image.<br/>
      iv. Click **Add**.

     <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/add-journey-variable.png" alt="drawing" width="60%"/>

13. Go to **Agent** > click **Preview** to test and display the dynamic image.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/test-dynamic-image.png)    
<!--     
This how the image will be fetch and displayed in cards format:


   ![](https://cdn.yellowmessenger.com/assets/yellow-docs/cards-display.png)
         -->

-------

### Get Feedback input

Use **Get feedback input** to collect feedback from users during conversation. This action allows you to capture ratings using either a thumbs up and thumbs down, or star rating. The feedback data is stored in the [User feedback](https://docs.yellow.ai/docs/cookbooks/insights/eventdescriptions#user-feedback) table in the Data Explorer and will be available throughout the session.

:::note
The **Get feedback input** action is currently available only for the Chat Widget channel.
:::

The table below describes the fields available in the Get feedback input action:

Field name | Description
-----------|------------
**Input name** | Define the name of the input field where the user's feedback will be stored.
**Data type** | Default data type is Object, as the feedback includes structured data (rating and comments).
**Description** | Specify the question or context for which you want to collect feedback. **Example**: "How would you rate your chat experience?".
**Feedback type** | Choose the rating format: <br/>• **Thumbs Up & Down** – Allows users to express satisfaction or dissatisfaction. <br/>• **Stars** – Enables users to provide detailed feedback on a 5-star scale.
**Allow additional comments** | Enable this option to allow users provide extra comments or feedback along with their rating.
**Ask for specific feedback for the rating** | Enable this option to ask follow-up questions based on the rating. You can customize questions and provide predefined reply options to understand the reason behind the customer’s rating.


<img src="https://cdn.yellowmessenger.com/assets/yellow-docs/get-feedback.png" alt="drawing" width="60%"/>

#### How to configure Feedback input

To configure and display Feedback input in your AI agent conversation, follow these steps:

1. Go to **Prompts** section and click **Actions** > **Get input**.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/create-input.png)
     
2. Select the **Feddback** action.

    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/sel-feedback.png" alt="drawing" width="50%"/>

3. In **Input name**, enter a unique name for the feedback input.
4. In **Description**, provide details about what feedback you want to collect from the user such as feedback on the conversation or service experience. **Example:** "How would you rate your chat experience?".
5. In **Select feedback type**, choose your preferred feedback form (type):
       1. **Thumbs Up & Down** – Allows users to give quick positive or negative feedback.
       2. **Stars** – Allows users to rate their experience on a scale (for example, 1 to 5 stars).
6. **Allow additional comments**: Enable this option to allow users to add extra comments or suggestions along with their rating.
7. **Ask for specific feedback for the rating**: Enable this option to collect **detailed feedback** from users based on their rating (positive or negative).  
You can customize both the **question** and **reply options** for each rating type.

   #### 1. **Thumbs up / Thumbs down**

    Choose whether to configure the question for a **positive** (👍) or **negative** (👎) rating. Each rating type can have its own **question** and **reply options**.

    | Field | Description | Example |
    |--------|--------------|----------|
    | **Question** | Follow-up question that appears after a user provides their rating. | "Tell us what you liked?" for positive feedback (👍) or "What went wrong?" for negative feedback (👎). |
   | **Reply options** | Predefined responses that users can select. You can add multiple options. | "Liked overall experience" or "Helpful agent". |
   | **➕ Add option** | Click **+** to add more reply options. | Add "Response not clear" or "Issue not resolved". |


   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/feedback1.png" alt="thumb feedback UI" width="60%"/>


   #### 2. Star Rating

   Displays a **rating scale** (for example, 1–5 stars).  
You can define different feedback questions for each rating level (example, **5 stars- positive**, **1–2 stars- needs improvement**).

   | Field | Description | Example |
   |--------|--------------|----------|
   | **Question** | The question asked based on the star rating provided. | "Tell us what you liked?"" or "What could be improved?"" |
   | **Reply options** | Predefined answers users can select after rating. | "Experience was good", "Quick response", or "Helpful support". |
   | **➕ Add option** | Click **+** to add more reply options. | Add "Response not clear" or "Issue not resolved". |

   <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/start-rating.png" alt="star rating UI" width="60%"/>
      
8. Click **Save**.

9. Click **Preview** to test and display the feedback option.
    
    <img src="https://cdn.yellowmessenger.com/assets/yellow-docs/feedback-rating.png" alt="drawing" width="60%"/>

10. Navigate to **Data Explorer** > **User feedback** table to view the collected feedback.

    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/userfeednac1.png)
    




      

   


  






