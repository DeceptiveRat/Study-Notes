The difference lies in the **way SQLMap receives the HTTP request information**. Here's why saving the POST request using Burp Suite and running `sqlmap` with `-r test.sql` works better in many cases:

### 1. **Request Details**
   - When you run SQLMap without specifying a request file, it makes its own HTTP requests to the target website. This might miss some specific details about the requests needed to exploit the vulnerability effectively.
   - By saving the POST request using Burp Suite, you're capturing **exactly how the web application communicates**, including the headers, cookies, POST data, and other parameters.

### 2. **Handling POST Requests**
   - Many vulnerabilities are found in POST requests (e.g., form submissions, API calls). If you don't specify the POST data, SQLMap might not correctly target the parameters involved in the POST request.
   - Using a saved request file ensures that SQLMap knows exactly what data to send in the body of the POST request.

### 3. **Custom Headers and Cookies**
   - Websites often use session cookies or specific headers for authentication, which might not be captured if you simply point SQLMap at the URL.
   - The saved request file from Burp Suite includes all the necessary headers and cookies, ensuring SQLMap can replicate the request as the web application expects.

### 4. **Precision Targeting**
   - The `-r` flag tells SQLMap to use the exact request from the file, giving it more context about the attack surface, such as parameters in the POST data or specific query formats.
   - Without this, SQLMap might not correctly identify injectable parameters or might miss the actual endpoint entirely.

### Example Scenario
Let’s say you’re testing a login page:
- Running `sqlmap -u http://example.com/login` might not capture the required POST data, such as `username=admin&password=123`.
- By capturing the request with Burp Suite and saving it as `test.sql`, you ensure that SQLMap gets the correct body data, headers, and cookies to process the request properly.

### Summary
Saving the POST request and running SQLMap with `-r test.sql` provides the tool with more precise and complete information about how the client communicates with the server, increasing the chances of finding SQL injection vulnerabilities.