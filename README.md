# 🛍️ Amazon Web Scraper Project

## 🎯 Project Objective
The goal of this project is to automatically scrape the product title and price from a specific Amazon product page at regular intervals, save the data along with a timestamp to a CSV file, and create a dataset that allows tracking price changes over time. The project demonstrates skills in web scraping, data processing, and automation.

## 🛠️ Technologies & Libraries Used
- Python
- `requests`
- `BeautifulSoup`
- `csv`
- `datetime`
- `time`
- `pandas` *(for optional data inspection)*
- `smtplib` *(for optional email alerts)*

## ⚙️ Core Functionalities

### 🔗 Connecting to the URL
- Uses the `requests` library to send a request to the specified Amazon product URL.

### 🛡️ Browser Spoofing
- To bypass Amazon's anti-scraping measures, HTTP headers (like `User-Agent`) are used to mimic a real browser.

### 🧠 HTML Parsing
- The raw HTML content returned from the page is parsed using the `BeautifulSoup` library.

### 📝 Data Extraction
- The product title is extracted using `id="productTitle"` and the price using `id="priceblock_ourprice"` (or similar identifiers).
- `.get_text()` is used to retrieve text content from the elements.

### 🧹 Basic Data Cleaning
- `.strip()` is used to remove unnecessary whitespace.
- Currency symbols (e.g., `$`) are stripped from the price values.

### ⏱️ Timestamping
- The `datetime` module is used to capture the exact date and time when the data was collected.

## 🗃️ Writing to CSV
- The `csv` module is used.
- On the first run, a CSV file is created with the headers: `('Title', 'Price', 'Date')`.
- On subsequent runs, the script appends a new row with the latest data.
- Uses `newline=''` and `encoding='UTF8'` for clean writing.

## 🔁 Automation Loop
- The script runs inside a `while True:` loop.
- A function like `check_price()` encapsulates the scraping and writing logic.
- `time.sleep()` is used to set the interval between runs (e.g., every 86400 seconds = once per day).

## 🔎 Data Reading & Monitoring
- The resulting CSV file can be read and analyzed using the `pandas` library.

## 📧 Optional Enhancement
- With `smtplib`, the project can send an email alert when the price drops below a defined threshold (a later step in the tutorial).

## 📌 Note
This project serves as a foundation for building automated price monitoring systems in e-commerce using Python.
