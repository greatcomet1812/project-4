# UOCIS322 - Project 4

Author: Sewon Sohn\
Contact: ssohn@uoregon.edu

This project calculates the open and close times for each specified checkpoints of the brevet given its distance and the starting time.

## Docker
To run the program with Docker, first build a Docker image in the same directory as the Dockerfile. 
Then, start a container from the Docker image, mapping the container's port 500 to the host's port 5001 (-p 5001:5000).\
The command `python -B $IMAGE` will run as specified in the Dockerfile with the default argument `flask_brevets.py` unless otherwise specified.
Access the service from the host machine at http://localhost:5001, which opens the template page.

## Application 
On the web page showing ACP Brevet Times, Select the brevet distance and set the beginning date and time.\
Then in the table below, put in checkpoints from 0 to the brevet distance (or up to 20% beyond).\
These users inputs are taken by AJAX in the template and passed into a function in the python Flask (`flask_brevets.py`),
which passes the data as parameters into functions called from `acp_times.py`.\
The functions `open_time` and `close_time` are called, which calculate the open and close times of the checkpoint specified as a parameter.\
The functions each return an arrow object of the open/close time, which is converted to JSON data that is sent back to the AJAX. 
The times are displayed in the designated format in the table.\
When the user increments or decrements the control distance, the input values will change, hence the times displayed will as well.
