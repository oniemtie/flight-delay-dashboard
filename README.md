Install python packages required to run the application. Copy and paste the below command to the terminal
python3 -m pip install packaging
python3 -m pip install pandas dash
pip3 install httpx==0.20 dash plotly

Create a new python script, by clicking on the side tool bar explorer icon and selecting new file icon, as shown in the image below.

# Import required libraries
import pandas as pd
import plotly.graph_objects as go
import dash
from dash import dcc
from dash import html
from dash.dependencies import Input, Output
import plotly.express as px


# Read the airline data into pandas dataframe (find public data)

Next, we create a skeleton for our dash application. Our dashboard application layout has three components as seen before:

Title of the application
Component to enter input year inside a layout division
5 Charts conveying the different types of flight delay
Mapping to the respective Dash HTML tags:

Title added using html.H1() tag
Layout division added using html.Div() and input component added using dcc.Input() tag inside the layout division.
5 charts split into three segments. Each segment has a layout division added using html.Div() and chart added using dcc.Graph() tag inside the layout division.
Copy the below code to the flight_delay.py script and review the structure.



Application title
Title as Flight Delay Time Statistics, align text as center, color as #503D36, and font size as 30.
Input component
Update dcc.Input component id as input-year, default value as 2010, and type as number. Use style parameter and assign height of the input box to be 35px and font-size to be 30.
Output component - Segment 1
Segment 1 is the first html.Div(). We have two inner division where first two graphs will be placed.

The core idea of this application is to get year as user input and update the dashboard in real-time. We will be using callback function for the same.

Steps:

Define the callback decorator
Define the callback function that uses the input provided to perform the computation
Create graph and return it as an output
Run the application

Callback decorator
We have 5 output components added in a list. Update output component id parameter with the ids provided in the dcc.Graph() component and set the component property as figure. One sample has been added to the skeleton.
Update input component id parameter with the id provided in the dcc.Input() component and component property as value.
Callback function
Next is to update the get_graph function. We have already added a function compute_info that will perform computation on the data using the input.

Mapping the returned value from the function compute_info to graph:

avg_car - input for carrier delay
avg_weather - input for weather delay
avg_NAS - input for NAS delay
avg_sec - input for security delay
avg_late - input for late aircraft delay





