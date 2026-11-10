# Amazon Web Scraping

Scrapes the **best-selling smartphones** list from [Amazon.in Best Sellers](https://www.amazon.in/gp/bestsellers/electronics/1805560031) with Python, and saves the results to CSV.

Amazon updates this list hourly based on sales, so each run captures a snapshot of what's selling right now.

## What it collects

For each of the 30 phones on each of the 8 pages, it saves:

| Column | Example |
|---|---|
| Description | Phone name and specs |
| Rating | 4.1 out of 5 stars |
| Reviews | Number of customer reviews |
| Price | Current price in ₹ |
| Link | Product page URL |

That's 240 rows in total, written to a CSV file.

## How it works

1. Build the URLs for pages 1–8 of the best-seller list
2. Download each page with `requests` (with a browser-like User-Agent header)
3. Parse the HTML with **Beautiful Soup** and pull out each phone's details from its tags
4. Collect everything into a dictionary of lists, then a **pandas** DataFrame
5. Save the DataFrame to CSV

## How to run

```bash
pip install requests beautifulsoup4 pandas
jupyter notebook "Scraping Best Selling Mobiles on Amazon.ipynb"
```

## Notes

Amazon's page layout and class names change often, and Amazon may block automated requests. If fields come back empty, the tag selectors in the notebook need updating.

## Future work

- Visit each phone's product page to collect more details
- Code optimisation and better documentation
- Try Selenium or Scrapy, since the page is dynamic and changes frequently

## Technologies

Python, Requests, Beautiful Soup, pandas, Jupyter Notebook

## References

- [Requests](https://requests.readthedocs.io/en/latest/), [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), [pandas](https://pandas.pydata.org/docs/)
- [Amazon web scraping tutorial (DataCamp)](https://www.datacamp.com/tutorial/amazon-web-scraping-using-beautifulsoup)
