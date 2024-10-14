# Phone Numbers API Endpoints

The Phone Numbers API provides endpoints for managing phone numbers within the Pia AI system. All endpoints require authentication using a Bearer token.

## Endpoints

### 1. Create Phone Number
- **Method:** POST
- **Path:** `/phone_numbers`
- **Description:** Acquires a new phone number and links it to AI agents for handling calls.
- **Request Body:** One of `CreateByoPhoneNumberDTO`, `CreateTwilioPhoneNumberDTO`, or `CreatePiaPhoneNumberDTO`
- **Response:** Returns the created phone number object (ByoPhoneNumber, TwilioPhoneNumber, or PiaPhoneNumber) with a 201 status code on success.

### 2. Get Phone Number Details
- **Method:** GET
- **Path:** `/phone_numbers/{id}`
- **Description:** Retrieves comprehensive information about a specific phone number.
- **Path Parameter:** `id` (string)
- **Response:** Returns the phone number object (ByoPhoneNumber, TwilioPhoneNumber, or PiaPhoneNumber) with a 200 status code on success.

### 3. Update Phone Number
- **Method:** PATCH
- **Path:** `/phone_numbers/{id}`
- **Description:** Updates the configuration of an existing phone number.
- **Path Parameter:** `id` (string)
- **Request Body:** `UpdatePhoneNumberDTO`
- **Response:** Returns the updated phone number object with a 200 status code on success.

### 4. Delete Phone Number
- **Method:** DELETE
- **Path:** `/phone_numbers/{id}`
- **Description:** Deletes an existing phone number.
- **Path Parameter:** `id` (string)
- **Response:** Returns a success message with a 200 status code on successful deletion.

### 5. List Phone Numbers
- **Method:** GET
- **Path:** `/phone_numbers`
- **Description:** Retrieves a paginated list of all phone numbers associated with the account.
- **Query Parameters:**
  - `page_size` (integer, 1-100, default 20): Number of results per page
  - `page_token` (string): Token for retrieving the next page
- **Response:** Returns an object containing:
  - `phone_numbers`: Array of phone number objects (ByoPhoneNumber, TwilioPhoneNumber, or PiaPhoneNumber)
  - `next_page_token`: Token for the next page of results

## General Information

- All endpoints use JSON for request and response bodies.
- The API uses standard HTTP status codes to indicate success or failure of requests.
- Error responses follow a consistent format defined in the `ErrorResponse` schema.
- The phone number objects (ByoPhoneNumber, TwilioPhoneNumber, PiaPhoneNumber) include properties such as id, provider, phone_number, ai_agent_id, and created_at.
- The creation requests allow for specifying different types of phone numbers (BYO, Twilio, or Pia) with their respective configurations.
- The update request allows for modifying the AI agent associated with a phone number.
