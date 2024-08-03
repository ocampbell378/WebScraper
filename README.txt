Web Scraper for Blog Titles and Dates
Project Overview
This project is a simple Python web scraper designed to extract and display blog post titles and publication dates from the PixelFord website's blog section. It uses the requests library to retrieve the webpage's HTML content and the BeautifulSoup library from bs4 to parse the HTML and extract relevant information.
Features
Retrieves blog post titles and publication dates.
Formats the publication dates into a human-readable format (e.g., "Aug 03 2024").
Outputs the results in a clean and easy-to-read format.
Requirements
Python 3.x
requests library
beautifulsoup4 library
Installation
Clone this repository to your local machine.
Ensure you have Python 3.x installed on your system.
Install the required Python libraries by running the following command:
bash
Copy code
pip install requests beautifulsoup4
Usage
Open the script file and ensure the URL variable is set to the desired webpage you wish to scrape. By default, it is set to https://pixelford.com/blog/.
Run the script using the following command:
bash
Copy code
python web_scraper.py
The script will output the blog titles and publication dates in the "Month Day Year - Title" format.
Code Explanation
Below is a brief explanation of the code:
Python
Copy code
import requests
from bs4 import BeautifulSoup
import datetime

# URL of the blog page to scrape
url = "https://pixelford.com/blog/"

# Send a GET request to the URL with a custom user-agent to avoid default user-agent blocking
response = requests.get(URL, headers={'user-agent: 'unique_string_to_bypass_defaut_user_agent'})

# Parse the HTML content using BeautifulSoup
html = response.content
soup = BeautifulSoup(html, 'html.parser')

# Find all article elements with the class 'type-post'
blogs = soup.find_all('article', class_='type-post')

# Loop through each blog post and extract the title and publication date
for blog in blogs:
    title = blog.find('a', class_='entry-title-link').get_text()

    # Extract and format the publication date
    blog_datetime_string = blog.find('time', class_='entry-time').get('datetime')
    blog_datetime = datetime.datetime.fromisoformat(blog_datetime_string)
    pretty_date = blog_datetime.strftime('%b %d %Y')

    # Print the formatted date and title
    print(f"{pretty_date} - {title}")
Note
The script assumes that the blog page's structure remains consistent. If the webpage's structure changes, you may need to update the HTML parsing logic.
The user-agent string is set to bypass any blocks against default user-agents. Modify it as needed for different websites.
