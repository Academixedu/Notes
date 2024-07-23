Here are some assignments based on the provided code examples and concepts:

### Assignment 1: Adding Request Parameters
**Task:** Modify the existing `hello` endpoint to include a new request parameter `greeting`, which will allow customizing the greeting message.

**Instructions:**
1. Update the `JavaController` to include a new request parameter `greeting` with a default value of "Hello".
2. Modify the method to return a message in the format: `<greeting>, <name>!`.



**Postman Testing:**
1. Create a new GET request.
2. Enter the URL: `http://localhost:8080/hello?name=John&greeting=Hi`.
3. Click on Send.
4. Check the response: You should see "Hi, John!".

### Assignment 2: Using Path Variables
**Task:** Create a new endpoint `/goodbye/{name}` that returns a goodbye message.

**Instructions:**
1. Add a new method in the `JavaController` that uses a path variable `name`.
2. The method should return a message in the format: "Goodbye, <name>!".



**Postman Testing:**
1. Create a new GET request.
2. Enter the URL: `http://localhost:8080/goodbye/John`.
3. Click on Send.
4. Check the response: You should see "Goodbye, John!".

### Assignment 3: Handling POST Requests
**Task:** Create a new endpoint `/welcome` that accepts a JSON object with `firstName` and `lastName`, and returns a welcome message.

**Instructions:**
1. Create a new method in the `JavaController` that handles POST requests and accepts a `Person` object.
2. The method should return a message in the format: "Welcome, <firstName> <lastName>!".



**Postman Testing:**
1. Create a new POST request.
2. Enter the URL: `http://localhost:8080/welcome`.
3. Go to the Body tab and select raw and JSON format.
4. Enter the JSON data:
   ```json
   {
       "firstName": "John",
       "lastName": "Doe"
   }
   ```
5. Click on Send.
6. Check the response: You should see "Welcome, John Doe!".

### Assignment 4: Working with JSON Responses
**Task:** Create a new endpoint `/status` that returns a JSON response with `status` and `message`.

**Instructions:**
1. Add a new method in the `JavaController` that returns a `Status` object.
2. The `Status` object should have `status` and `message` fields.
3. The method should return a message in the format: `{ "status": "success", "message": "Service is running" }`.



**Postman Testing:**
1. Create a new GET request.
2. Enter the URL: `http://localhost:8080/status`.
3. Click on Send.
4. Check the response: You should see a JSON object:
   ```json
   {
       "status": "success",
       "message": "Service is running"
   }
   ```

