import datetime
import time

# Infinite loop printing increasing count every 0.5 seconds (commented out to avoid blocking)
# count = 1
# while True:
#     print(count)
#     count += 1 
#     time.sleep(0.5)

# Get current datetime
x = datetime.datetime.now()

# Create a specific datetime object: May 17, 2020, 20:45:30
x = datetime.datetime(2020, 5, 17, 20, 45, 30)

# Print the datetime object
print(x)

# Print the weekday number (Monday=0, Sunday=6)
print(x.weekday())

# Infinite loop printing current datetime every 2 seconds (commented out to avoid blocking)
# while True:
#     print(datetime.datetime.now())
#     time.sleep(2)

# ================================================================================
# Exercise 01: Create datetime object from user input and check if it's a weekend

new_day = datetime.datetime(int(input("year : ")), int(input("month: ")), int(input("day: ")))

# Check if the date is Thursday (3) or Friday (4), considered weekends
if new_day.weekday() == 3 or new_day.weekday() == 4:
    print("this date is weekend")
    print("5sh" if new_day.weekday() == 3 else "jomas")  # Print '5sh' for Thursday, 'jomas' for Friday
else:
    print("this date is working day")

# ================================================================================
# Python datetime formatting example

x = datetime.datetime(2020, 5, 17, 20, 45, 30)

print(x)

# Format datetime to string: Year/Month/Day Weekday Hour:Minute AM/PM
print(x.strftime("%Y/%b/%d %A %I:%M %p"))

# ================================================================================
# pickle library usage (notes)
# 'dump' means save data to file
# 'load' means read data from file

# ================================================================================
# json library usage

import json

# Example dictionary to convert to JSON string
x = {
    "name" : "pouya",
    "age" : 18,
    "city" : "new york"
}

# Convert dictionary to JSON string
y = json.dumps(x)

# Print JSON string
print(y)

# Save JSON string to a file named "name.json"
open("name.json", "w").write(y)

# ===============================================================================================
# Reading a JSON file example

# JSON string example
date = '{"name": "pouya", "age": 18, "city": "new york"}'

# Read JSON string from file "name.json"
date = open("name.json", "r").read()

# Convert JSON string back to Python dictionary
date_new = json.loads(date)

# Print value of the "name" key
print(date_new["name"])

# ==============================================================================================
# JSON pretty printing with indentation

x = {
    "name" : "pouya",
    "age" : 18,
    "city" : "new york"
}

# Convert dictionary to JSON string without indentation
y = json.dumps(x)

# Convert dictionary to JSON string with indentation for readability
y = json.dumps(x, indent=4)

# Print formatted JSON string
print(y)

# ==============================================================================================
# Web scraping using requests

import requests

# Send HTTP GET request to specified URL
respons = requests.get("http://www.ostadkhalili.ir")

# Print response object (shows status code)
print(respons)

# ==============================================================================================
# Web scraping with BeautifulSoup

from bs4 import BeautifulSoup  # Import parser library

url = "https://pypi.org/project/beautifulsoup4/"

# Send HTTP GET request to URL
respons = requests.get(url)

# Print response object and raw HTML text
print(respons)
print(respons.text)

# Parse HTML content using html.parser
soup = BeautifulSoup(respons.text, "html.parser")

# Find all <div> elements with class "text"
soup_text = soup.find_all("div", class_="text")

# Print number of matched elements
print(len(soup_text))

# Print all matched elements as list
print(soup_text)

# These next lines will cause errors because soup_text is a list, not a soup object
# new_soup1 = soup_text.find_all("div", class_="text")  
# new_soup2 = soup_text.find("div", class_="text")     
# new_soup3 = soup_text.find_all("span")               

# Print length of the list and length of second element (if possible)
print(len(soup_text))
print(len(soup_text[1]))

# Loop through each element and print the element and its text content
for s in soup_text:
    print(s)
    print(s.text)

# =============================================================================================
# Divar website scraping example

url = "https://divar.ir/s/shiraz/buy-residential"

# Send GET request
respons = requests.get(url)

# Parse the response HTML
soup = BeautifulSoup(respons.text, "html.parser")

# Find first div with class "widget-col-d2306"
soup_text = soup.find("div", class_="widget-col-d2306")

# Or find all divs with that class
soup_text = soup.find_all("div", class_="widget-col-d2306")

# Find all divs with class "Kt-post-card__description"
soup_text = soup.find_all("div", class_="Kt-post-card__description")

# Print how many matched elements were found
print(len(soup_text))

# Print the text of each element, then stop after first
for s in soup_text:
    print(s.text)
    print("---------------------------------------")
    break
