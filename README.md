# PSU Masters Sample Backend/API

- **Objective** - Implementat a sample API using Express, MongoDb, and Swagger

# To Run

- Once respository is cloned locally, user can run either of these commands:
  - **node index.js** - runs server locally; will need to stop, save, and re-run when modifying
  - **npm start** - runs server locally; automatically re-runs after saving

# NPM packages to install

- **npm init -y** - setup new project and creates package.json
- **npm install express** - installs express
- **npm install mongodb** - installs mongodb
- **npm i mongoose** - installs mongoose
- **npm i dotenv** - installs dotenv (used for environment variables)
- **npm install --save-dev nodemon** - installs nodemon
- **npm install yamljs** - installs yaml
- **npm install swagger-ui-express** - installs swagger UI
- **npm install axios** - installs axios (used to make request to 3rd party API)

# Additional Resources

- Tutorial to setup Express and MongoDb
  - youtube.com/watch?v=30p9QfybWZg/
- Mongoose queries
  - https://www.geeksforgeeks.org/mongoose-queries/

# Code Walkthrough

- index.js
  - ![image](https://github.com/user-attachments/assets/3d9e227f-cb58-4dd8-96dc-fbf9c5f54f13)
    - The required libraries needed for Express, MongoDb, and Swagger
    - Initializing express and using .env file for setting the port and mongodb url
    - Setting up swagger for "/api-docs" endpoint
    - Connecting to mongodb and using the PORT from env
  - ![image](https://github.com/user-attachments/assets/5b212a68-06bb-492a-926a-2e664f748f1a)
    - GET endpoints
    - "/" returns a welcome message
    - "/users" returns all users with 200 response or 500 response if there is server error
    - "/users/:id/" returns one user based on id with 200 response, 404 if user cannot be found, or 500 if there is a server error
  - ![image](https://github.com/user-attachments/assets/50b6237d-3964-4ae8-b80a-0690923ead5f)
    - POST endpoint
    - "/users" creates a new user with 201 response, 400 if the body fails validation, or 500 if there is server error
  - ![image](https://github.com/user-attachments/assets/31418e23-53a3-4a56-b5f8-cd1ffdc23eae)
    - PUT endpoint
    - "/users/:id" updates an existing user with 200 response, 404 if user cannot be found, 400 if the body fails validation, or 500 if there is a server error
  - ![image](https://github.com/user-attachments/assets/2703cc9b-7d75-424b-8553-602ac1a8eb69)
    - DELETE endpoint
    - "/users/:id" deletes an existing user with 200 response, 404 if user cannot be found, or 500 if there is a server error
- user.js
  - ![image](https://github.com/user-attachments/assets/e98b74e4-7a67-4647-8610-b932d6b85c80)
    - Defines the User schema
    - Makes certain fields required
- swagger.yaml
  - ![image](https://github.com/user-attachments/assets/3d62324c-ce5f-4773-aec9-238a2327c89f)
    - Defines how Swagger UI will appear
   
# Functionality Demo

- GET Request
  - ![image](https://github.com/user-attachments/assets/46e105a0-4e5b-4d39-94c5-d4ff54d0cdc3)
  - ![image](https://github.com/user-attachments/assets/14649ccd-bb4e-44c4-8134-85f770226325)
  - ![image](https://github.com/user-attachments/assets/34ae6054-2440-4aec-a724-e5154cb50dc4)
- POST Request
  - ![image](https://github.com/user-attachments/assets/0dcd8df0-a9bb-409a-ac1d-508ed2d386a1)
  - ![image](https://github.com/user-attachments/assets/2f8b58fa-04ec-43f5-a717-d0e740e01908)
  - ![image](https://github.com/user-attachments/assets/f37d7c13-007f-455d-970c-c1daf51e9854)
- PUT Request
  - ![image](https://github.com/user-attachments/assets/0b917626-1877-4ab3-a637-2cb55d6546ea)
  - ![image](https://github.com/user-attachments/assets/3128ad5f-9049-4170-8957-47da479755b6)
  - ![image](https://github.com/user-attachments/assets/94aba0c5-a818-4711-83dd-06fcea2cf85b)
- DELETE
  -   ![image](https://github.com/user-attachments/assets/5a929cb7-a1d3-44f7-a13f-6087fd47acdf)
  -   ![image](https://github.com/user-attachments/assets/f21a02b3-1c6a-4244-be1b-df24604048cb)
  -   ![image](https://github.com/user-attachments/assets/0c301f49-918a-406f-bacc-ab6875eb2d08)
- Swagger UI
  - ![image](https://github.com/user-attachments/assets/68249759-10ce-4fc4-bd49-55f1c4492744)
  - ![image](https://github.com/user-attachments/assets/95b660ec-4836-4691-aea1-6ed0f7e69c3e)
  - ![image](https://github.com/user-attachments/assets/ec5d5f84-e583-439b-9a06-e5e794d97193)
  - ![image](https://github.com/user-attachments/assets/1aa23ac1-c5b9-491f-bc3a-95a2372f2f75)
  - ![image](https://github.com/user-attachments/assets/7e2acca9-4041-4a0b-ac34-b320c286188d)
  - ![image](https://github.com/user-attachments/assets/4dac1106-d436-48a7-92b3-206418710d63)
- MongoDB
  - ![image](https://github.com/user-attachments/assets/31f6f600-430f-45af-8684-cead3790cd85)

# Consuming 3rd Party API

- The GET request for "/harry-potter-houses" makes a request to https://wizard-world-api.herokuapp.com/Houses/805fd37a-65ae-4fe5-b336-d767b8b7c73a which returns House Ravenclaw from its API
- The response from wizard-world-api is validated to ensure it has all of the required fields in the HarryPotterHouseSchema before being saved to HarryPotterHouse collection in MongoDB
  - ![image](https://github.com/user-attachments/assets/15e5ab82-8ec3-4491-b681-3fc0cccf288c)
  - ![image](https://github.com/user-attachments/assets/9ce4bebb-943b-4c94-8c23-62ca696f950c)
  - ![image](https://github.com/user-attachments/assets/fd20872c-2906-45eb-b0dc-2a7deac7d2db)
  - ![image](https://github.com/user-attachments/assets/d68b5f02-071c-4abe-a1bf-34e931c73b8c)
  - ![image](https://github.com/user-attachments/assets/b65d50a7-f7c4-4754-a60e-15c82135153a)











 
