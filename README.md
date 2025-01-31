# Web Scraping Project: Extracting Data from FactsOnActs

This project is designed to scrape data from the website [FactsOnActs](https://www.factsonacts.nl). It uses **Selenium** and **Python** to extract key information, such as category, title, website link, and email address. The data is organized by category and saved in an Excel file with separate sheets for each category.

## Project Structure

```
.
├── scraped_data_parallel.xlsx   # Excel file with scraped data organized by category
├── scraper.py                   # Main Python script for scraping data
└── README.md                    # This README file
```

## Prerequisites

Ensure you have the following Python libraries installed:

- `selenium` – Web scraping framework
- `pandas` – Data manipulation and analysis
- `re` – Regular expressions (standard Python library)
- `concurrent.futures` – For parallel processing

You can install the necessary dependencies using `pip`:

```bash
pip install selenium pandas
```

Also, make sure you have [Chromedriver](https://sites.google.com/a/chromium.org/chromedriver/) installed and available in your system PATH.

## Features

- **Parallel Scraping**: The script scrapes multiple pages concurrently using `concurrent.futures.ThreadPoolExecutor` to speed up the data extraction process.
- **Data Extraction**: Extracts categories, titles, website links, and email addresses from each webpage.
- **Data Organization**: Data is saved in an Excel file with each category in a separate sheet.
- **Sanitization**: Sheet names are sanitized to remove any invalid characters, and sheet names are truncated to 31 characters to comply with Excel's naming limitations.

## How to Use

1. Clone or download the repository.
2. Modify the `scraper.py` script to include the correct path to your `chromedriver` executable.
3. Run the script:

```bash
python scraper.py
```

4. After the script finishes, it will generate an Excel file (`scraped_data_parallel.xlsx`) with the extracted data organized by category.

## Script Details

### `scraper.py`

The script does the following:

1. **Sets up a headless Selenium WebDriver**: The script uses the Chrome browser in headless mode (without a UI) to scrape data.
2. **Extracts Data**: For each URL in the list, it extracts:
   - Category
   - Title of each item
   - Website link
   - Email link (if available)
3. **Processes URLs in Parallel**: The script uses the `ThreadPoolExecutor` from `concurrent.futures` to process multiple URLs concurrently, significantly improving the speed of scraping.
4. **Sanitizes Sheet Names**: Excel sheet names are sanitized to remove invalid characters like `[]:*?/\\` and truncated to 31 characters.
5. **Saves Data to Excel**: The scraped data is stored in an Excel file, where each category gets its own sheet.

## Example Output

The generated `scraped_data_parallel.xlsx` will look like this:

- Each sheet represents a category.
- Inside each sheet, the columns are:
  - **Category**: The category of the scraped data.
  - **Title**: The title of the item.
  - **Website**: The website URL.
  - **Email**: The email address (if available).

## Notes

- Ensure that you have the correct path for your `chromedriver` executable.
- The script uses `time.sleep()` to give the website some time to load elements; you might need to adjust the delay depending on your internet speed and the responsiveness of the website.
- The script is optimized for concurrency using `ThreadPoolExecutor`, allowing for faster scraping when working with multiple URLs.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
