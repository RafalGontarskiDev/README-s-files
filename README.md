## 3. Available Methods

### 1. **Stripe Checkout: List All Checkout Sessions**

- **Description:** This action calls the API [List All Checkout Sessions](https://stripe.com/docs/api/checkout/sessions/list) to retrieve a list of all Checkout sessions associated with your Stripe account.

#### How to Use

1. **Prepare action in Your logic:**  
   Design the logic to include optional filters like date, status, or other parameters for narrowing the results.

**Logic Example:**  
![LOGIC]()

2. **Result:**  
   The **RESPONSE** will contain a list of Checkout sessions with their details.

#### Expected Response

- Returns a list of Checkout sessions, including their IDs, payment status, and session modes.

**Response Example:**  
![RESPONSE]()

---

### 2. **Stripe Checkout: Create a Session**

- **Description:** This action calls the API [Create a Session](https://stripe.com/docs/api/checkout/sessions/create) to generate a new Stripe Checkout session for handling payments or subscriptions.

#### How to Use

1. **Prepare action in Your logic:**  
   Design the logic to include necessary details like `line_items`, `success_url`, `cancel_url`, and payment method preferences.

**Logic Example:**  
![LOGIC]()

2. **Result:**  
   The **RESPONSE** will contain the session details, including its unique ID and status.

#### Expected Response

- Returns details of the created Checkout session, such as its ID, URL, and payment status.

**Response Example:**  
![RESPONSE]()

---

### 3. **Stripe Checkout: Retrieve a Checkout Session's Line Items**

- **Description:** This action calls the API [Retrieve Line Items](https://stripe.com/docs/api/checkout/sessions/line_items) to fetch the line items (products or services) associated with a specific Checkout session.

#### How to Use

1. **Prepare action in Your logic:**  
   Design the logic to include the `sessionId` of the Checkout session.

**Logic Example:**  
![LOGIC]()

2. **Result:**  
   The **RESPONSE** will include the details of the products or services purchased in the specified session.

#### Expected Response

- Returns the line items associated with the specified Checkout session.

**Response Example:**  
![RESPONSE]()

---

### 4. **Stripe Checkout: Retrieve a Session**

- **Description:** This action calls the API [Retrieve a Session](https://stripe.com/docs/api/checkout/sessions/retrieve) to get full details about a specific Checkout session.

#### How to Use

1. **Prepare action in Your logic:**  
   Design the logic to include the `sessionId` of the Checkout session.

**Logic Example:**  
![LOGIC]()

2. **Result:**  
   The **RESPONSE** will contain details about the session, such as payment status, customer data, and session mode.

#### Expected Response

- Returns full details of the Checkout session, including customer information and payment status.

**Response Example:**  
![RESPONSE]()

---

### 5. **Stripe Checkout: Expire a Session**

- **Description:** This action calls the API [Expire a Session](https://stripe.com/docs/api/checkout/sessions/expire) to manually expire an active Checkout session.

#### How to Use

1. **Prepare action in Your logic:**  
   Design the logic to include the `sessionId` of the session you want to expire.

**Logic Example:**  
![LOGIC]()

2. **Result:**  
   The **RESPONSE** will confirm the expiration of the session.

#### Expected Response

- Confirms that the session has been successfully expired.

**Response Example:**  
![RESPONSE]()

---

### Status Codes Overview

For each method in this documentation, the **RESPONSE** will include a **STATUS** field. The possible status codes are:

- **`"OK"`**: The request was successful.
- **`"BAD_REQUEST"`**: The request was malformed or contained invalid data.
- **`"UNAUTHORIZED"`**: The provided API key does not have sufficient permissions.
- **`"NOT_FOUND"`**: The specified resource could not be found.

These status codes will appear consistently in the **Result** section of each method and will indicate the outcome of the API request.
