---
title: Get started with Markdoc
description: How to get started with API
---

#### Get Started

# Welcome to FastAPI

This Documentation provides comprehensive information about the Toggl API, including endpoints, request formats, authentication, and usage guidelines. Developers can use this documentation to integrate Toggl’s time tracking and reporting services into their applications.

## Quick start

Let’s break down the key sections, endpoints, parameters, examples for the “Make Toingg” POST method in the Toggl API documentation.

<!-- If you want to get started right away with this boilerplate, either clone the [GitHub repository](https://github.com/markdoc/markdoc-starter) or deploy a version of this site to Vercel by clicking the button below.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/markdoc/markdoc-starter) -->

## 1. Make Tonigg

<!-- If you'd prefer to start from scratch, feel free to check out the [official repository](https://github.com/markdoc/markdoc) and [documentation site](https://markdoc.dev/docs/getting-started). -->

- **Endpoint** : POST `/make/toingg`
- **Description** : This endpoint allows you to perform a specific action related to the “Toingg” feature called Add makeCallData.

### Parameters:

- **`ApiKey`** : send as a Parameter

### Request Body:

```
{
  "campaign": "string",
  "numberList": [
    {
      "clientName": "string",
      "clientNumber": "string"
    }
  ]
}
```

![Image](https://www.kennethlange.com/wp-content/uploads/2018/10/task_api.png)

### Example Request (Using Axios in React.js):

First, make sure you have the `axios` library installed in your React.js project:

```
npm install axios
```

Next, create a function to make the API call using `axios`:

```
import axios from 'axios';

const makeToinggRequest = async () => {
  try {
    const response = await axios.post(
      'https://call.toingg.com/api/make/toingg',
      {
        "campaign": "string",
        "name": "string",
        "phoneNumber": "string"
      },
      {
        headers: {
          'Content-Type': 'application/json',
          Authorization: 'Basic API_TOKEN:api_token', // Replace with your actual API token
        },
      }
    );

    console.log('Response:', response.data);
    // Handle the response data as needed (e.g., update state, display a message)
  } catch (error) {
    console.error('Error making Toingg request:', error);
    // Handle errors (e.g., show an error message to the user)
  }
};

// Call the function wherever needed (e.g., in a button click handler)
// makeToinggRequest();

```

- Replace `API_TOKEN` with the actual user’s API token.
- Customize the request body with relevant parameters and values.

### Notes:

- The API accepts only JSON requests. Set `Content-Type: application/json` in your request header.
- Each request returns a JSON-encoded body.
- Times and dates use the ISO 8601 standard.
- Rate limiting is implemented using a Leaky bucket mechanism.
- For more details, refer to the [Official Bland.AI API documentation](https://docs.bland.ai/api-v1/post/calls-simple).

![Image](https://www.devopsschool.com/blog/wp-content/uploads/2020/04/curl-http-rest-api-request-response.jpg)

---

## Make Call Details:

- **Endpoint** : POST `/make_toingg_details`
- **Description** : Make a call with specific details (campaign name, script, name, and phone number).

### Parameters:

- **`ApiKey`** : Sent as a parameter.

### Request Body:

```
{
  "campaignName": "MyCampaign",
  "campaignScript": "Hello, this is a test call.",
  "name": "John Doe",
  "phoneNumber": "+1234567890"
}
```

### Example in React.js:

```
import axios from 'axios';

const makeCallDetails = async () => {
  const apiUrl = 'https://call.toingg.com/api/make_toingg_details'; // Replace with the actual API URL
  const apiKey = 'YOUR_API_KEY'; // Replace with your API key

  const data = {
    campaignName: 'MyCampaign',
    campaignScript: 'Hello, this is a test call.',
    name: 'John Doe',
    phoneNumber: '+1234567890'
  };

  try {
    const response = await axios.post(apiUrl, data, {
      headers: {
        Authorization: `Bearer ${apiKey}`,
        'Content-Type': 'application/json'
      }
    });
    console.log('Call details response:', response.data);
  } catch (error) {
    console.error('Error making call details:', error);
  }
};

// Call the function
makeCallDetails();
```

### Notes:

- Replace `YOUR_API_KEY` with your actual API key.
- Adjust the `data` object with your campaign name, campaignScript, name and phone number.

## Batch CallData:

- Endpoint: `/make_batch_toingg`
- Description: Make batch calls for multiple numbers within a campaign.

### Parameters:

- **`ApiKey`**: Sent as a parameter.

### Request Body:

```
{
  "campaign": "string",
  "numberList": [
    {
      "clientName": "string",
      "clientNumber": "string"
    }
  ]
}

```

### Example in React.js:

```
import axios from 'axios';

const makeBatchCall = async () => {
  const apiUrl = 'https://call.toingg.com/api/make_batch_toingg'; // Replace with the actual API URL
  const apiKey = 'YOUR_API_KEY'; // Replace with your API key

  const data = {
    campaign: 'MyCampaign',
    numberList: [
      {
        clientName: 'Client A',
        clientNumber: '+1234567890'
      },
      {
        clientName: 'Client B',
        clientNumber: '+9876543210'
      }
    ]
  };

  try {
    const response = await axios.post(apiUrl, data, {
      headers: {
        Authorization: `Bearer ${apiKey}`,
        'Content-Type': 'application/json'
      }
    });
    console.log('Batch call response:', response.data);
  } catch (error) {
    console.error('Error making batch call:', error);
  }
};

// Call the function
makeBatchCall();
```

### Notes:

- Replace `YOUR_API_KEY` with your actual API key.
- Adjust the `data` object with your campaign and numberList.

## 2. Send SMS :

- **Endpoint** : `/send_sms`
- **Description** : Send an SMS message

### Parameters:

- **`ApiKey`** : Sent as a parameter.

### Request Body:

```
{
  "name": "John Doe",
  "phoneNumber": "+1234567890",
  "message": "Hello from Toggl!"
}
```

### Example in React.js:

```
import axios from 'axios';

const sendSMS = async () => {
  const apiUrl = 'https://call.toingg.com/api/send_sms'; // Replace with the actual API URL
  const apiKey = 'YOUR_API_KEY'; // Replace with your API key

  const data = {
    name: 'John Doe',
    phoneNumber: '+1234567890',
    message: 'Hello from Toggl!'
  };

  try {
    const response = await axios.post(apiUrl, data, {
      headers: {
        Authorization: `Bearer ${apiKey}`,
        'Content-Type': 'application/json'
      }
    });
    console.log('SMS response:', response.data);
  } catch (error) {
    console.error('Error sending SMS:', error);
  }
};

// Call the function
sendSMS();
```

### Notes:

- Replace `YOUR_API_KEY` with your actual API key.
- Adjust the `data` object with your name, message and phone number.

## 3. Call Management Endpoints:

- **Endpoint** : `/hang_up_call`
- **Description** : This endpoint is used to hang up a call. It requires the following parameters

### Parameters:

- **`ApiKey`** : An API key for authentication.
- **callSid** : The unique identifier for the call session.

### Example in React.js:

```
// CallManagement.js

import React from 'react';

const HangUpCall = ({ callSid, apiKey }) => {
  const handleHangUp = async () => {
    try {
      // Make an API call to hang up the call
      const response = await fetch(`/hang_up_call?callSid=${callSid}&apiKey=${apiKey}`, {
        method: 'POST',
      });

      if (response.ok) {
        console.log('Call hung up successfully.');
      } else {
        console.error('Error hanging up the call.');
      }
    } catch (error) {
      console.error('An error occurred:', error);
    }
  };

  return (
    <button onClick={handleHangUp}>Hang Up Call</button>
  );
};

export default HangUpCall;

```

### Notes:

- Remember to replace the placeholders (callSid, apiKey, etc.) with actual values from your application. These examples demonstrate how to make API calls using React’s fetch function, but you can adapt them to your preferred HTTP library or framework.

## 4. Checkout Session Endpoints:

- **Endpoint** : `/create-checkout-session`
- **Description** : This endpoint creates a checkout session. It does not require any parameters in the URL. However, the request body should include the following:

### Request Body :

{
"apikey": "string"
}

### Example in React.js:

```
// CheckoutSession.js

import React from 'react';

const CreateCheckoutSession = ({ apiKey }) => {
  const handleCreateSession = async () => {
    try {
      // Make an API call to create a checkout session
      const response = await fetch('/create-checkout-session', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          apikey: apiKey,
        }),
      });

      if (response.ok) {
        const data = await response.json();
        console.log('Checkout session created:', data.sessionId);
      } else {
        console.error('Error creating checkout session.');
      }
    } catch (error) {
      console.error('An error occurred:', error);
    }
  };

  return (
    <button onClick={handleCreateSession}>Create Checkout Session</button>
  );
};

export default CreateCheckoutSession;

```

### Notes:

- Remember to replace the placeholders (callSid, apiKey, etc.) with actual values from your application. These examples demonstrate how to make API calls using React’s fetch function, but you can adapt them to your preferred HTTP library or framework.

## 5. Stripe Webhook Endpoints:

- **Endpoint** : `/webhook`
- **Description** : This endpoint is where Stripe will send real-time event data related to your Stripe account. It allows your application to react to events such as successful payments, disputes, recurring payment updates, and more.

#### Side Menu

- [1. Make Tonigg](#section1)
- [2. Send SMS ](#section2)
- [3. Call Management Endpoints ](#section3)
- [4. Checkout Session Endpoints ](#section4)
- [5. Stripe Webhook Endpoints: ](#section5)
