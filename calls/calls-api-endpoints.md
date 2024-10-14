# Calls API Endpoints

The Calls API provides endpoints for managing phone and web calls within the Pia AI system. All endpoints require authentication using a Bearer token.

## Endpoints

### 1. Create Phone Call
- **Method:** POST
- **Path:** `/create-phone-call`
- **Description:** Initiates a new outbound phone call.
- **Request Body:** `CreatePhoneCallRequest` (includes from_number, to_number, and optional parameters)
- **Response:** Returns the created `PhoneCallResponse` object with a 201 status code on success.

### 2. Create Web Call
- **Method:** POST
- **Path:** `/create-web-call`
- **Description:** Initiates a new web-based call session.
- **Request Body:** `CreateWebCallRequest` (includes ai_agent_id and optional parameters)
- **Response:** Returns the created `WebCallResponse` object with a 201 status code on success.

### 3. Get Call Details
- **Method:** GET
- **Path:** `/calls/{call_id}`
- **Description:** Retrieves detailed information about a specific call.
- **Path Parameter:** `call_id` (string)
- **Response:** Returns either a `WebCallResponse` or `PhoneCallResponse` object based on the call type.

### 4. List Calls
- **Method:** GET
- **Path:** `/calls`
- **Description:** Retrieves a paginated list of call records matching specified criteria.
- **Query Parameters:**
  - `ai_agent_ids` (array of strings): List of AI agent IDs to filter by
  - `start_time_before` (date-time): Upper bound for call start time
  - `start_time_after` (date-time): Lower bound for call start time
  - `end_time_before` (date-time): Upper bound for call end time
  - `end_time_after` (date-time): Lower bound for call end time
  - `sort_direction` (string, "asc" or "desc", default "desc"): Sort direction by timestamp
  - `page_size` (integer, default 100): Number of results per page
  - `page_token` (string): Token for retrieving the next page
- **Response:** Returns an object containing:
  - `calls`: Array of `WebCallResponse` or `PhoneCallResponse` objects
  - `next_page_token`: Token for the next page of results

## General Information

- All endpoints use JSON for request and response bodies.
- The API uses standard HTTP status codes to indicate success or failure of requests.
- Error responses follow a consistent format defined in the `ErrorResponse` schema.
- The `WebCallResponse` and `PhoneCallResponse` schemas include various properties such as call_id, ai_agent_id, call_status, transcripts, and call-specific details.
- The creation requests allow for specifying call parameters and optional metadata.
