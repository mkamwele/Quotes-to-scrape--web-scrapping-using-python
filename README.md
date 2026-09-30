# Quotes-to-scrape--web-scrapping-using-python
# Quotes to Scrape — Web Scraping Project

## Overview

This project practices web scraping with Python using [Quotes to Scrape](https://quotes.toscrape.com/).

The goal was to scrape quotes from the website's **Top 10 tags**, handle pages with multiple pages of quotes, and collect information about the authors.

## Tools Used

* Python
* Requests
* BeautifulSoup
* Pandas
* `urllib.parse.urljoin()`

## What I Scraped

For each quote, I collected:

* Tag
* Quote
* Author
* Author URL
* Author birth date
* Author birth location

## Scraping Process

The project followed these steps:

1. Request the Quotes to Scrape homepage.
2. Find the **Top 10 tags**.
3. Extract the URL for each tag.
4. Visit each tag page.
5. Extract the quotes and authors.
6. Handle pagination by following the **Next** button.
7. Extract the author's profile URL.
8. Visit each author's page.
9. Extract the author's birth date and birth location.
10. Store the scraped information in Pandas DataFrames.
11. Merge the quote and author information using the author's URL.

## Pagination

Some tags contain more than one page of quotes.

I used a `while` loop to continue scraping until there was no **Next** button:

```python
while current_url:
    # scrape current page

    # find next page

    # continue or stop
```

This allowed the scraper to collect quotes from all available pages for each tag.

## Avoiding Duplicate Author Requests

An author can have multiple quotes, so the same author URL may appear many times.

To avoid repeatedly scraping the same author page, I first collected the unique author URLs and then scraped each author page once.

## Final Dataset

The final dataset connects quote information with author information:

| Column           | Description                   |
| ---------------- | ----------------------------- |
| `Tag`            | Tag associated with the quote |
| `Quote`          | Quote text                    |
| `Author`         | Name of the author            |
| `Author_url`     | Link to the author's page     |
| `Born Date`      | Author's birth date           |
| `Birth Location` | Author's birth location       |

## Key Concepts Practiced

This project helped me practice:

* Sending HTTP requests with `requests`
* Parsing HTML with BeautifulSoup
* Finding HTML elements using tags and classes
* Extracting text and links
* Working with relative URLs using `urljoin()`
* Handling pagination
* Using nested `for` and `while` loops
* Storing scraped data in lists and dictionaries
* Creating Pandas DataFrames
* Removing duplicate URLs with `.unique()`
* Combining DataFrames with `merge()`

## Next Step

The next part of the project will explore **authenticated web scraping**, including:

* Login forms
* CSRF tokens
* `requests.Session()`
* Cookies
* Login requests
* Accessing pages that require authentication
