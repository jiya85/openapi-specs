# PIA LLMs API Endpoints

The PIA LLMs API provides endpoints for managing Language Learning Models (LLMs) within the Pia AI system. All endpoints require authentication using a Bearer token.

## Endpoints

### 1. Create LLM
- **Method:** POST
- **Path:** `/llms`
- **Description:** Creates a new PIA LLM.
- **Request Body:** `CreatePiaLLMDTO` (varies based on LLM type: simple, agentic, or custom)
- **Response:** Returns the created `PiaLLM` object with a 201 status code on success.

### 2. Get LLM
- **Method:** GET
- **Path:** `/llms/{llm_id}`
- **Description:** Retrieves a specific PIA LLM by its ID.
- **Path Parameter:** `llm_id` (UUID)
- **Response:** Returns the `PiaLLM` object on success (200) or a 404 error if not found.

### 3. Update LLM
- **Method:** PUT
- **Path:** `/llms/{llm_id}`
- **Description:** Updates an existing PIA LLM.
- **Path Parameter:** `llm_id` (UUID)
- **Request Body:** `UpdatePiaLLMDTO` (varies based on LLM type)
- **Response:** Returns the updated `PiaLLM` object on success (200), 404 if not found, or 400 for bad requests.

### 4. Delete LLM
- **Method:** DELETE
- **Path:** `/llms/{llm_id}`
- **Description:** Deletes a specific PIA LLM by its ID.
- **Path Parameter:** `llm_id` (UUID)
- **Response:** Returns a 204 status code on successful deletion or 404 if not found.

### 5. List LLMs
- **Method:** GET
- **Path:** `/llms`
- **Description:** Retrieves a paginated list of PIA LLMs.
- **Query Parameters:**
  - `page_size` (integer, 1-100, default 20): Number of results per page
  - `page_token` (string): Token for retrieving the next page
  - `sort_direction` (string, "asc" or "desc", default "desc"): Sort direction by timestamp
- **Response:** Returns an object containing:
  - `llms`: Array of `PiaLLM` objects
  - `next_page_token`: Token for the next page of results
  - `pagination_info`: Object with pagination details

## General Information

- All endpoints use JSON for request and response bodies.
- The API uses standard HTTP status codes to indicate success or failure of requests.
- Error responses follow a consistent format defined in the `ErrorResponse` schema.
- The `PiaLLM` schema includes different types of LLMs (simple, agentic, and custom), each with its specific properties.
- The creation and update DTOs reflect these different LLM types, allowing for type-specific data to be sent when creating or updating LLMs.
