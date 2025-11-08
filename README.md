# **Web Scraping \- US Largest Private Companies by Revenue**

## **1\. Overview**

This is a Python script that demonstrates a simple and powerful method for web scraping using the pandas and requests libraries. The goal is to fetch the "List of largest companies in the United States by revenue" page from Wikipedia, parse its content, and extract the table of **Largest private companies** into a clean, structured pandas DataFrame.

This notebook shows an efficient alternative to manual HTML parsing by leveraging the built-in pd.read\_html() function.

## **2\. Dataset**

The data is scraped live from a single source:

* **Source:** Wikipedia  
* **URL:** https://en.wikipedia.org/wiki/List\_of\_largest\_companies\_in\_the\_United\_States\_by\_revenue

The target data is the *second* table on the page, titled "Largest private companies".

## **3\. Tools Used**

* **Python 3**  
* **Requests:** For sending HTTP requests to fetch the webpage.  
* **Pandas:** For reading the HTML table directly into a DataFrame and performing data cleaning.  
* **lxml:** (Implicitly required by pd.read\_html) As the high-performance parser for pd.read\_html.

## **4\. Scraping Process**

The script (WebScarping.ipynb) follows these key steps:

1. **Import Libraries:** Import pandas and requests.  
2. **Provide User-Agent:** A User-Agent header is set to mimic a real web browser (like Chrome). This is a critical step to avoid being blocked by Wikipedia's servers.  
3. **Fetch HTML:** A try...except block is used to send an HTTP GET request to the target URL. response.raise\_for\_status() ensures that an error is raised if the page fails to load.  
4. **Parse Tables with Pandas:** The pd.read\_html() function is used on the response.text. This powerful function automatically finds *all* tables on the page and returns them as a list of DataFrames.  
5. **Select Correct Table:** After inspecting the list of tables, the correct DataFrame (containing the private companies) is selected by its index. On this page, it is the second table, so df \= tables\[1\].  
6. **Clean Data:** The resulting DataFrame is cleaned by dropping any unnecessary or unnamed columns (e.g., Unnamed: 0\) that may have been created during the import.  
7. **Display Results:** The .head() and .describe() methods are used to show the final, clean DataFrame.

## **5\. Results**

The final output of this project is a clean, structured pandas DataFrame containing the largest US private companies by revenue.

DataFrame Head (Example):  
| Rank | Name | Industry | Revenue (USD billions) | Employees | Headquarters |  
| :--- | :--- | :--- | :--- | :--- | :--- |  
| 1 | Cargill | Food industry | 177.0 | 160,000 | Minnetonka, Minnesota |  
| 2 | Koch Industries | Conglomerate | 125.0 | 120,000 | Wichita, Kansas |  
| 3 | Publix Super Markets | Retail | 54.5 | 250,000 | Lakeland, Florida |  
| ... | ... | ... | ... | ... | ... |

## **6\. How to Run**

1. **Clone the Repository:**  
   git clone \[your-repository-url\]  
   cd \[repository-name\]

2. **Set up Environment:**  
   * It is recommended to use a virtual environment.  
   * Install the required libraries:  
     pip install pandas requests lxml  
