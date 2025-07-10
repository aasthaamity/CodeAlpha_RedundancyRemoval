

This code snippet demonstrates how to interact with a Firebase Realtime Database:

import firebase_admin, from firebase_admin import credentials, db, from firebase_admin import _apps: These lines import the necessary libraries for working with Firebase Admin SDK.
cred = credentials.Certificate(...): This line loads your Firebase service account credentials from a JSON file. These credentials are used to authenticate your application with Firebase. Make sure to replace "redundancyremoval-52de0-firebase-adminsdk-fbsvc-afb47e3240.json" with the actual path to your credentials file.
if 'my_app' not in _apps: firebase_admin.initialize_app(...): This block checks if a Firebase app with the name 'my_app' has already been initialized. If not, it initializes the app with the provided credentials and database URL. This prevents errors if you run the cell multiple times.
ref = db.reference("users", app=firebase_admin.get_app('my_app')): This line gets a reference to the "users" node in your Firebase Realtime Database. The app=firebase_admin.get_app('my_app') part ensures that you are using the specifically named app.
def is_duplicate(email): ...: This function checks if a user with the given email already exists in the "users" node of the database. It retrieves all users and iterates through them to compare emails.
def add_user(name, email, phone): ...: This function adds a new user to the "users" node. Before adding, it calls is_duplicate() to check if a user with the same email already exists. If not, it pushes the new user data to the database and prints a success message. Otherwise, it prints a duplicate message.
add_user("Aastha", "aastha@email.com", "1234567890"): This is an example of how to use the add_user function to add a new user to the database.
This code essentially provides a simple way to manage user data in your Firebase Realtime Database, preventing the addition of users with duplicate emails.
