<h1 align="center">NODEJS-HW-07</h1>

<p align="center">Comprehensive API Documentation with Swagger/OpenAPI</p>

<p align="center">
  <!-- Dynamic badges - You may need to customize these for your specific GitHub repository -->
  <img src="https://img.shields.io/github/last-commit/emrealtnts0/nodejs-hw-07?color=blue&label=last%20commit" alt="Last Commit">
  <img src="https://img.shields.io/github/languages/top/emrealtnts0/nodejs-hw-07?color=orange&label=JavaScript" alt="JavaScript Percentage">
  <img src="https://img.shields.io/github/languages/count/emrealtnts0/nodejs-hw-07?color=green&label=languages" alt="Languages Count">
</p>

<p align="center">Built with the tools and technologies for API Documentation:</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express.js">
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB">
  <img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm">
  <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black" alt="Swagger">
  <img src="https://img.shields.io/badge/OpenAPI-6BA53B?style=for-the-badge&logo=openapi&logoColor=white" alt="OpenAPI">
  <img src="https://img.shields.io/badge/ReDocly-FF5252?style=for-the-badge&logo=redocly&logoColor=white" alt="ReDocly">
  <img src="https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white" alt="YAML">
</p>

## 🎯 Task: API Documentation with Swagger/OpenAPI

This project focuses on implementing comprehensive API documentation using Swagger/OpenAPI for an existing Node.js Express application. The goal is to enhance API clarity and ease of use through well-structured and interactive documentation.

### Learning Objectives:

*   Setting up basic documentation configurations in Swagger.
*   Utilizing the `@redocly/cli` package for documentation generation.
*   Organizing and configuring API documentation.
*   Adding documentation for various API endpoints.

### Acceptance Criteria:

*   The task must be completed on the `hw7-swagger` branch.
*   Homework submission must include links on GitHub to source files and the deployed project (on `hw7-swagger` branch) via render.com.
*   No errors should occur when running the task code.
*   Adherence to the application file structure specified in the course materials.

## 🚀 Step-by-Step Task Implementation:

### Step 1: Branch Creation
Create the `hw7-swagger` branch from `hw6-email-and-images` and perform this task on the `hw7-swagger` branch.

### Step 2: Documentation Setup
1.  Install `@redocly/cli` as a Dev dependency:
    ```bash
    npm install @redocly/cli --save-dev
    ```
2.  Add new scripts to the `scripts` section in `package.json`:
    ```json
    {
      "scripts": {
        "build": "npm run build-docs",
        "build-docs": "redocly bundle --ext json -o docs/swagger.json",
        "preview-docs": "redocly preview-docs"
      }
    }
    ```
3.  Create `redocly.yaml` file with the following content:
    ```yaml
    # See <https://redocly.com/docs/cli/configuration/> for more information.
    apis:
      sample@v1:
        root: docs/openapi.yaml
    extends:
      - recommended
    rules:
      no-unused-components: error
    theme:
      htmlTemplate: ./docs/index.html
      colors:
        primary:
          main: '#32329f'
      generateCodeSamples:
        languages:
          - lang: curl
          - lang: Node.js
          - lang: JavaScript
    ```
4.  Create a `docs` folder in the project root, and inside it, create `index.html` with the following content:
    ```html
    <!DOCTYPE html>
    <html>

    <head>
      <meta charset="utf-8">
      <title>API Reference | ReDoc</title>
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link rel="icon" type="image/png" href="favicon.png">
      <style>
        body {
          margin: 0;
          padding: 0;
        }
      </style>
      {{{redocHead}}}
    </head>

    <body>
      {{{redocHTML}}}
    </body>

    </html>
    ```
5.  Create `docs/openapi.yaml` file with the following content:
    ```yaml
    openapi: 3.1.0
    info:
      version: 1.0.0
      title: <your_application_name>
      license:
        name: Apache 2.0
        url: http://www.apache.org/licenses/LICENSE-2.0.html
      description: >
        <your_application_description>
    tags:
      # tags you will use
    servers:
      - url: http://localhost:3000
      - url: #link_to_deployed_site
    paths:
      # endpoint links will be here
    components:
      securitySchemes:
        bearerAuth:
          type: http
          scheme: bearer
    ```
    You can see your changes by running `npm run preview-docs` command.

### Step 3: Documentation Structure
Create a `swagger` folder. Inside this folder, add two folders: `components` and `paths`. In the `components` folder, store parts of entities such as responses or entity descriptions. In the `paths` folder, store documentation according to the path structure. For example, for the `GET /contacts/:contactId` route, the corresponding file will be `/swagger/paths/contacts/{id}/get.yaml`.

### Step 4: Document `GET /contacts/:contactId`
Add documentation for the `GET /contacts/:contactId` route to the corresponding file. Its content should include:
- `tags` — The tag this endpoint belongs to (e.g., Contacts).
- `summary` — Short description of the endpoint.
- `operationId` — Unique operation ID.
- `description` — More detailed description.
- `security` — Indicate that we use authentication with Bearer token.
- `parameters` — Request parameters (for this endpoint, the path parameter `:contactId`).
- `responses` — Response options:
    - 200 Successful response.
    - 404 Not Found response.
Add the link to this endpoint in the `./docs/openapi.yaml` file.

### Step 5: Document Other Endpoints
Using the same principle, add documentation for the following endpoints:
- `GET /contacts`
- `PATCH /contacts/:contactId`
- `DELETE /contacts/:contactId`
- `POST /contacts`
Remember to include query parameters for `GET /contacts` and body descriptions for requests containing them.

### Step 6 (Optional): Document Authentication Endpoints
Optionally, write documentation for authentication endpoints.

### Step 7: Integrate Swagger UI
Add a separate route `/api-docs` and display the documentation using the `swagger-ui-express` package.

### Step 8: Deploy to Render.com
Change the branch for project deployment on render.com to `hw7-swagger`. Ensure the changes are successfully deployed.

This task will help you create useful and informative documentation for your API. Good luck with completing the task! 🚀
