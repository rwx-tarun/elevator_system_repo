# Elevator System

This is a Django project that simulates a simplified elevator system. It allows for the initialization of N elevators, and each elevator can move up and down, open and close its door, start and stop running,  display its floor, take requests from user and return the most optimal elevator.

## APIs
- POST /initialize - Initializes the elevator system with N elevators.
- GET /elevator_request/<elevator_id>/ - Returns a list of requests for a given elevator.
- GET /elevator_request/destination_floor - Returns the next destination floor for a given elevator.
- GET /elevator/get_elevator_direction - Returns whether the elevator is moving up or down currently.
- POST /elevator_request/ - Saves user request to the list of requests for a given elevator.
- POST /elevator_request/mark_elevator_operational/ - Marks an elevator as not working or in maintenance.
- POST /elevator_request/door_operation/ - Opens/Close the elevator door.

## Architecture
The project is built using Django and Django Rest Framework. It uses Model-View-Controller (MVC) architecture. The models hold the data for the elevators and requests, views handle the requests, and controllers perform the business logic.

## Database Modelling
The project uses an SQLLite database to store elevator and request data. The models are as follows:


## Models 
### ElevatorRequest
  - Represents a request made to the elevator system from a particular floor.
  - Contains the floor number where the request was made.
  - Has a default object to be used when no other elevator request is available.

### Elevator
  - Represents an individual elevator in the elevator system.
  Has a boolean field for whether the elevator is operational or not.
  - Tracks the current floor of the elevator.
  - Tracks the direction the elevator is moving in (up, down, or stopped).
  - Tracks whether the elevator doors are open or closed.
  - Has a many-to-many relationship with ElevatorRequest to track which requests have been assigned to it.
  - Belongs to a Building object.

### Building
  - Represents the overall building containing the elevator system.
  - Has a default number of floors (5).
  - Has a field for the number of elevators in the building.


## Setup and Deployment
- Clone the repository to your local machine:
```bash
 git clone git@github.com:rwx-tarun/elevator_system_repo.git
```
- Create a virtual environment and activate it:
Copy code
```bash
virtualenv env 
```
```bash 
source env/bin/activate
```
Install the dependencies: 
```bash
pip install -r requirements.txt
```
Run the database migrations: 
```bash
python manage.py makemigrations
python manage.py migrate
```

Start the Django development server:
```bash
python manage.py runserver
```
To use the APIs, make requests to the appropriate endpoints using a tool like Postman or a web browser.

### [Postman Collection Link](https://drive.google.com/file/d/1mhmYy9DNPCNQUgzD4lRUcM0BpJ2_6Iqp/view?usp=share_link)

Import the collection in postman run server and you are good to go !!!.
### Thank You 


