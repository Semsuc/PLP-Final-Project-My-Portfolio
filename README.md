# PLP-Final-Project-My-Portfolio
Portfolio Website with Contact Form
This is a personal portfolio website that includes a contact form. The website allows users to send messages through the contact form, which are saved to a MySQL database and also sent to a designated email address using Nodemailer. The backend server is built with Node.js and Express, while the frontend consists of HTML, CSS, and JavaScript.

Features
Portfolio Display: Main portfolio page served through Express.
Contact Form: A form that allows users to submit their name, email, and a message.
Message Storage: Submitted messages are stored in a MySQL database.
Email Notifications: Submitted messages are emailed to the owner using Nodemailer.
Message Logging: Each submitted message is logged to a local file for future reference.
Requirements
Node.js (v14.x or above)
MySQL
A Gmail account for email sending via Nodemailer
Setup Instructions
1. Clone the Repository
First, clone the project repository to your local machine.

bash
Copy code
git clone https://github.com/yourusername/portfolio-website.git
cd portfolio-website
2. Install Dependencies
Install the required Node.js dependencies by running the following command:

bash
Copy code
npm install
The dependencies include:

express: A minimal and flexible Node.js web application framework.
nodemailer: A module for sending emails from Node.js.
mysql: A module for interacting with a MySQL database.
dotenv: A module for managing environment variables.
3. Configure Environment Variables
Create a .env file in the root directory of the project. Add the following configuration to it:

env
Copy code
DB_HOST=localhost
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=your_db_name
DB_PORT=3306
PORT=8000
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_password
DB_HOST: Your MySQL host (usually localhost).
DB_USER: Your MySQL username.
DB_PASSWORD: Your MySQL password.
DB_NAME: The name of your MySQL database.
DB_PORT: The port your MySQL server is running on (default is 3306).
PORT: The port on which your Node.js server will run (default is 8000).
EMAIL_USER: Your Gmail email address (for sending contact form emails).
EMAIL_PASS: Your Gmail app password (you must generate an app password from your Google Account settings).
4. Set Up MySQL Database
Open MySQL and create a database for your project:

sql
Copy code
CREATE DATABASE your_db_name;
Create a table for storing contact messages:

sql
Copy code
CREATE TABLE messages (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  message TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
5. Start the Server
Once you've set up your environment, you can start the server by running:

bash
Copy code
node server.js
The server will start and listen on the port specified in the .env file (default is port 8000).

6. Access the Portfolio Website
After starting the server, open your browser and go to:

arduino
Copy code
http://localhost:8000
This will display your portfolio page. You can test the contact form by submitting a message.

7. Submitting a Message
When a user submits the form on the contact page, the message is sent to the specified email address (via Gmail) and saved to the MySQL database.
Additionally, the submitted message is logged to a local file messages.txt.
Project Structure
bash
Copy code
portfolio-website/
│
├── public/                # Static files (HTML, CSS, JS, Images)
│   ├── index.html         # Main portfolio page
│   ├── styles.css         # Styles for the portfolio page
│   └── scripts.js         # Client-side JavaScript for the form
│
├── server.js              # Server-side code (Node.js + Express)
├── .env                   # Environment variables for MySQL and email
├── messages.txt           # Logs submitted messages
├── package.json           # Project metadata and dependencies
└── README.md              # This file
Technologies Used
Node.js: JavaScript runtime for building the server.
Express: Web framework for Node.js.
MySQL: Database for storing contact form messages.
Nodemailer: Module for sending email notifications.
dotenv: Module for managing environment variables.
JavaScript: Client-side scripting for form validation and AJAX handling.
Troubleshooting
1. Database Connection Error
If you encounter a database connection error, check that your MySQL server is running and the credentials in the .env file are correct.

2. Email Not Sending
If the email isn't sending:

Make sure the email credentials in the .env file are correct.
Ensure that your Gmail account has allowed less secure apps or generate an app password for Nodemailer to use.
3. CORS Issues
If your frontend and backend are running on different ports, you may encounter CORS issues. To solve this, add CORS support to your server:

js
Copy code
const cors = require('cors');
app.use(cors());  // Allow all origins (for development)
4. Form Validation
If the form submission fails because required fields (name, email, or message) are missing, ensure all fields are filled correctly before submitting.
