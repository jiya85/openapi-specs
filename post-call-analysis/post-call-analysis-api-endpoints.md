# Post-Call Analysis API Endpoints

The Post-Call Analysis API provides endpoints for managing and retrieving call analysis items within the Pia AI system. All endpoints require authentication using a Bearer token.

## Endpoints

### 1. Create Call Analysis
- **Method:** POST
- **Path:** `/ai_agents/{agent_id}/analysis`
- **Description:** Creates new analysis items for a specific AI agent.
- **Path Parameter:** `agent_id` (string)
- **Request Body:** Array of `PostCallAnalysisItem` objects
- **Response:** Returns a success message with a 201 status code on successful creation.

### 2. Update Call Analysis
- **Method:** PUT
- **Path:** `/ai_agents/{agent_id}/analysis`
- **Description:** Updates existing analysis items for a specific AI agent.
- **Path Parameter:** `agent_id` (string)
- **Request Body:** Array of `PostCallAnalysisItem` objects
- **Response:** Returns a success message with a 200 status code on successful update.

### 3. Delete Call Analysis
- **Method:** DELETE
- **Path:** `/ai_agents/{agent_id}/analysis`
- **Description:** Deletes existing analysis items for a specific AI agent.
- **Path Parameter:** `agent_id` (string)
- **Request Body:** Array of strings (IDs of the analysis items to be deleted)
- **Response:** Returns a success message with a 200 status code on successful deletion.

### 4. Retrieve Call Analysis
- **Method:** GET
- **Path:** `/calls/{call_id}/analysis`
- **Description:** Retrieves detailed analysis information about a specific call.
- **Path Parameter:** `call_id` (string)
- **Response:** Returns an array of `PostCallAnalysisResult` objects with a 200 status code on success.

## General Information

- All endpoints use JSON for request and response bodies.
- The API uses standard HTTP status codes to indicate success or failure of requests.
- Error responses follow a consistent format defined in the `ErrorResponse` schema.
- The `PostCallAnalysisItem` schema includes different types of analysis items (string, enum, boolean, number), each with its specific properties.
- The `PostCallAnalysisResult` schema represents the result of a post-call analysis item, which can be a string, boolean, or number depending on the analysis item type.
- Create, Update, and Delete operations are performed on the AI agent level, while retrieval is done for individual calls.
