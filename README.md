# duo_postman_api_collections
**Overview**

This repository contains Postman collections and environment configurations to interact with the Duo Admin API for managing users, groups, authentication logs, applications, and more.

The collection is designed to help security administrators and developers test and automate administrative tasks within Duo Security.


**Prerequisites**

Before using this collection, ensure you have:

Duo Admin panel Access:

You need API credentials (Integration Key, Secret Key, and API Hostname) for the [Admin API](https://duo.com/docs/adminapi), [Auth API](https://duo.com/docs/authapi), [OIDC API](https://duo.com/docs/oauthapi), and [UNIX](https://duo.com/docs/loginduo).

Enable Admin API in the Duo Admin Panel.

The API requires Duo MFA with an Admin role enabled.

Postman Installed:

Download Postman.

Newman Installed (for CLI execution, optional):

bash
Copy
Edit
npm install -g newman
Setup & Installation
1. Clone Repository
bash
Copy
Edit
git clone https://github.com/your-repo-name.git
cd your-repo-name
2. Import Postman Collection & Environment
Open Postman → Click Import → Select the collection JSON file (Duo-Admin-API-Collection.json).

Import the environment JSON (Duo-Environment.json).

3. Configure Environment Variables
Set the following environment variables in Postman:

Variable Name	Description	Example
DUO_API_HOSTNAME	Your Duo API hostname	api-xxxx.duosecurity.com
DUO_INTEGRATION_KEY	Your Integration Key	DIXXXXXXXXXXXXXXXXXX
DUO_SECRET_KEY	Your Secret Key (store securely)	xxxxxxxxxxxxxxxxxxxx
Authentication & Security
API Authentication
Duo Admin API uses HMAC-SHA1 request signing. Each request must include a properly formatted Authorization Header.

Postman pre-request scripts handle this automatically by generating:

The Date header.

The Signature using your Secret Key.

For manual API requests, refer to Duo Admin API Authentication.

Important Security Notes
Never share or expose your Secret Key in a public repository.

Use Postman’s variable encryption or store secrets securely.

If credentials are compromised, revoke & regenerate in Duo Admin Panel.

How to Use
Using Postman UI
Select the Duo-Admin-API-Collection in Postman.

Choose an API request (e.g., Get Users, Get Logs).

Ensure your environment is set with API credentials.

Click Send and view the response.

Using Newman CLI (Optional)
To run all requests via command line:

bash
Copy
Edit
newman run Duo-Admin-API-Collection.json -e Duo-Environment.json
To generate an HTML report:

bash
Copy
Edit
newman run Duo-Admin-API-Collection.json -e Duo-Environment.json -r html
Collection Structure
pgsql
Copy
Edit
/duo-admin-api-postman
│── collections/
│   ├── Duo-Admin-API-Collection.json
│── environments/
│   ├── Duo-Environment.json
│── scripts/
│   ├── auth-signature.js
│── README.md
collections/ → Contains the Postman collection for Duo Admin API.

environments/ → Stores the environment JSON file with API credentials.

scripts/ → Custom scripts for authentication and request signing.

