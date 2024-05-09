# MFA-PressData
| ![](READMEmedia/thunderclient_search.png) | <div align="center"><span style="font-size: large;">**MFA press statements scraped from official websites.<br><br>Separated by countries and dates.<br><br>Cleaned, processed, and ingested into Elasticsearch for easy searching and analysis.**</span></div> |
| --- | --- |

This project is part of PopFigExpert
## Data Collection and Processing
The press statements are collected using a custom web scraper implemented in Python and executed within a Jupyter notebook (`MFA Scrape.ipynb`). The notebook performs the following key steps:

1. **URL Configuration**: The notebook begins by defining the base URLs for the MFA websites to be scraped. This allows for easy modification and addition of new sources.

2. **Web Scraping**: Utilizing the powerful `requests` and `BeautifulSoup` libraries, the notebook navigates through each MFA website, locates the relevant press statement pages, and extracts the desired information, such as the statement text, date, and any available metadata. The scraper is designed to handle common web page structures and navigate pagination where necessary.

3. **Data Cleaning**: Once the raw data is collected, the notebook applies various data cleaning techniques to ensure consistency and remove any unwanted elements, such as HTML tags or special characters. This step is crucial for preparing the data for further analysis and storage.

4. **Text Processing**: The cleaned press statements undergo basic text processing tasks, such as tokenization, lowercasing, and removal of stopwords (if desired). These steps help normalize the text data and make it more suitable for text analysis techniques.

5. **Data Storage**: The processed press statements are then organized by country and date, with each statement saved as an individual text file following a standardized naming convention (`COUNTRY_YYYY-MM-DD.txt`). This structured storage approach facilitates easy retrieval and analysis of the data.

The Jupyter notebook provides a streamlined and efficient workflow for collecting, cleaning, and storing MFA press statements. By leveraging the power of Python and popular web scraping libraries, the notebook offers a reproducible and customizable solution for building a comprehensive database of diplomatic communications. This resource can be invaluable for researchers, analysts, and anyone interested in studying international relations and foreign policy.


## Data Structure

### TypeScript
```typescript
type ArticleSearchResult = {
  title: string;
  url: string;
  date: string;
  country: string;
  content: string;
}
```

### Elasticsearch index mappings
```python
index_mappings = {
  "mappings": {
    "properties": {
      "date": {"type": "date"},
      "title": {"type": "text"},
      "url": {"type": "text"},
      "country": {"type": "text"},
      "content": {"type": "text"},
    }
  }
}
```


## Dependencies
The notebook requires the following dependencies:

Python 3.x
Jupyter Notebook
Pandas
Requests
Langchain & Tiktoken to split text into chunks