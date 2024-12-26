Clone or download the repository:
git clone <repository_url>
cd <repository_directory>

Ensure Python is installed: This project requires Python 3.6 or higher. Verify the installation with:
python --version

Run the application: Execute the following command from the project directory:
python <script_name>.py

Access the API: Open a browser or use tools like Postman or curl to interact with the API at:
http://127.0.0.1:5000

Authenticate requests: Use the predefined token admin-token in the Authorization header for all requests:
Authorization: admin-token

Design Choices

In-Memory Database:
For simplicity, an in-memory dictionary (books and members) is used to store data. This avoids external dependencies like SQL or NoSQL databases but is not persistent across runs.

Token-Based Authentication:
A basic token-based mechanism ensures security by requiring a valid token (Authorization header) for all endpoints.

Tokens are predefined and stored in the users dictionary.

Pagination:
All list endpoints (GET /books and GET /members) support pagination via page and per_page query parameters to manage large datasets effectively.

Search Functionality:
The GET /books endpoint includes search capabilities by title and author using query parameters title and author.

Error Handling:
Returns appropriate HTTP status codes and error messages for invalid operations (e.g., 404 Not Found for nonexistent resources).

Scalability:
Although the in-memory approach is not scalable, the design supports easy migration to a database by replacing the books and members dictionaries with database calls.

Assumptions and Limitations

Authentication:

Tokens are hardcoded and not generated dynamically. For production, integrate a robust authentication mechanism (e.g., OAuth, JWT).

Data Persistence:

Data is not saved to disk and will be lost when the application stops. To make it persistent, integrate a database like SQLite, PostgreSQL, or MongoDB.

Validation:

Input validation is minimal. Add stricter validation to ensure data integrity (e.g., checking email formats or non-empty fields).

Performance:

The current design is suitable for small-scale applications. For large datasets, optimize search and pagination by using indexed database queries.

Multi-User Support:

Only a single admin user is predefined. Extend the users dictionary or use a user-management system for multi-user support.

API Endpoints

Books

GET /books: Retrieve a paginated list of books, with optional search by title and author.

GET /books/<book_id>: Retrieve details of a specific book.

POST /books: Add a new book.

PUT /books/<book_id>: Update an existing book.

DELETE /books/<book_id>: Delete a book.

Members

GET /members: Retrieve a paginated list of members.

GET /members/<member_id>: Retrieve details of a specific member.

POST /members: Add a new member.

PUT /members/<member_id>: Update an existing member.

DELETE /members/<member_id>: Delete a member.
