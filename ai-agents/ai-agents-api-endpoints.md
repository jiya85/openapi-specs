# AI Agents API Endpoints

The AI Agents API provides endpoints for managing AI agents within the Pia AI system. All endpoints require authentication using a Bearer token.

## Endpoints

### 1. Create AI Agent
- **Method:** POST
- **Path:** `/ai_agents`
- **Description:** Creates a new AI agent.
- **Request Body:** `CreateAIAgentRequest` (includes LLM ID, TTS and STT configurations, and various agent settings)
- **Response:** Returns the created `AIAgent` object with a 201 status code on success.

### 2. Get AI Agent
- **Method:** GET
- **Path:** `/ai_agents/{agent_id}`
- **Description:** Retrieves a specific AI agent by its ID.
- **Path Parameter:** `agent_id` (string)
- **Response:** Returns the `AIAgent` object on success (200) or a 404 error if not found.

### 3. Update AI Agent
- **Method:** PUT
- **Path:** `/ai_agents/{agent_id}`
- **Description:** Updates an existing AI agent.
- **Path Parameter:** `agent_id` (string)
- **Request Body:** `UpdateAIAgentRequest` (includes fields to be updated)
- **Response:** Returns the updated `AIAgent` object on success (200), 404 if not found, or 400 for bad requests.

### 4. Delete AI Agent
- **Method:** DELETE
- **Path:** `/ai_agents/{agent_id}`
- **Description:** Deletes a specific AI agent by its ID.
- **Path Parameter:** `agent_id` (string)
- **Response:** Returns a 204 status code on successful deletion or 404 if not found.

### 5. List AI Agents
- **Method:** GET
- **Path:** `/ai_agents`
- **Description:** Retrieves a paginated list of AI agents.
- **Query Parameters:**
  - `page_size` (integer, 1-100, default 20): Number of results per page
  - `page_token` (string): Token for retrieving the next page
- **Response:** Returns an object containing:
  - `data`: Array of `AIAgent` objects
  - `next_page_token`: Token for the next page of results

## General Information

- All endpoints use JSON for request and response bodies.
- The API uses standard HTTP status codes to indicate success or failure of requests.
- Error responses follow a consistent format defined in the `ErrorResponse` schema.
- The `AIAgent` schema includes various properties such as agent_id, llm_id, agent_name, TTS and STT configurations, and other agent-specific settings.
- The creation and update requests allow for specifying or modifying these AI agent properties.
