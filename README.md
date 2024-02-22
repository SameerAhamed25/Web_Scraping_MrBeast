# Web_Scraping_MrBeast

> Loading Web Pages with 'request'

The `requests` module allows you to send HTTP requests using Python.
The HTTP request returns a Response Object with all the response data (content, encoding, status, and so on). 
Get the contents of the URL using requests module
Store the text response in a variable called txt
Store the status code in a variable called status
Print txt and status using print function

> Extracting title with BeautifulSoup
Use the requests package to get title of the URL
Use BeautifulSoup to store the title of the page into a variable called page_title
once we feed the page.content inside BeautifulSoup, we can start working with the parsed DOM tree.

>  BS4 body and head
Repeat the experiment with URL
Store page title (without calling .text) of URL in `page_title`
Store body content (without calling .text) of URL in `page_body`
Store head content (without calling .text) of URL in `page_head`
When you try to print the page_body or page_head you'll see that those are printed as strings.
But in reality, when you print(type page_body) you'll see it is not a string but it works fine.

> select with BeautifulSoup
Once we have the soup variable, we can work with `.select` on it which is a CSS selector inside BeautifulSoup.
Create a variable, Set it to empty list.
Use `.select` to select all the tags and store the text of those tags inside variable list.

> Select DOM elements with BeautifulSoup methods.
scrape out their names and store them in a list called `top_items`.
Use `.select` to extract the titles.
Use `.select` to extract the review count label for those product titles. 
Use the `strip` method to remove any extra newlines/whitespaces you might have in the output.
Append this dictionary in a list called `top_items`
Print this list at the end

> Extracting Links
Extract the `href` attribute of links with their text as well. 
You have to create a list called `Extrected_links`
Make sure your text is stripped of any whitespace
Make sure you check if your `.text` is None before you call `.strip()` on it.
Store all these dicts in the `extracted_links`
Print this list at the end.

> Generating CSV from data
import requests
from bs4 import BeautifulSoup
import csv

1.Make a request to your website
page = requests.get("https://mrbeast.store/")
soup = BeautifulSoup(page.content, 'html.parser')

2.Create a list to store the extracted links
extracted_links = []

3.Extract links from various elements 
link_elements = soup.find_all(['a', 'link', 'area', 'img'])

4.Iterate through the elements and extract the 'href' attribute
for elem in link_elements:
    href = elem.get('href')
    if href:
        extracted_links.append(href)

5.Write the extracted links to a CSV file
with open('extracted_links.csv', 'w', newline='') as csvfile:
    csv_writer = csv.writer(csvfile)
    csv_writer.writerow(['Link'])  # Write header
    for link in extracted_links:
        csv_writer.writerow([link])

 6.print("CSV file 'extracted_links.csv' has been created.")


