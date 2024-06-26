# Investor Search and Analysis Tool

## Project Overview

This project is designed to help you identify potential investors based on their past investment activities in specific areas and industries. The tool automates the process of searching for investor information online, extracting relevant details, summarizing the information, and scoring the investors based on predefined criteria.

## Features

- **Automated Web Search**: Searches for each investor's name combined with specific search terms.
- **Web Scraping**: Extracts relevant investment details from the search results.
- **Summarization**: Uses OpenAI's GPT model to summarize the extracted information.
- **Scoring**: Ranks investors based on the number of investments and relevance to specified criteria.

## Prerequisites

- Python 3.6+
- OpenAI API key (for summarization)

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/investor-search-analysis.git
    cd investor-search-analysis
    ```

2. Install the required Python packages:

    ```sh
    pip install -r requirements.txt
    ```

## Configuration

1. **Set Up OpenAI API Key**:
    - Sign up for an OpenAI API key at [OpenAI](https://beta.openai.com/signup/).
    - Add your API key to the script in the `openai.api_key` variable.

## Usage

1. **Prepare the Input Data**:
    - Edit the `names` and `search_terms` lists in the script to include the names of the investors and the search terms relevant to your needs.

2. **Run the Script**:
    - Execute the script:

        ```sh
        python investor_search.py
        ```

3. **Review the Output**:
    - The script will output a list of investors sorted by their score, based on the number of relevant investments and other criteria.

## Script Details

### search_web(name, term)

- Performs a web search for the given name and search term.
- Returns the HTML content of the search results page.

### extract_investment_details(html)

- Parses the HTML content to extract relevant investment details.
- Returns a list of investments.

### summarize_investments(investments)

- Uses OpenAI's GPT model to summarize the list of investments.
- Returns a summary string.

### score_investments(summaries)

- Scores each investor based on the summarized investment details.
- Returns a dictionary of investors and their scores.

### Main Logic

- Iterates through each name and search term, performs the search, extracts details, summarizes the information, and scores the investors.
- Outputs a sorted list of investors based on their scores.

## Example

```python
# List of names and search terms
names = ["John Doe", "Jane Smith", "Richard Roe"]
search_terms = ["London", "investment", "joint venture"]

# OpenAI API key
openai.api_key = "YOUR_OPENAI_API_KEY"

# Run the main logic
summaries = {}
for name in names:
    for term in search_terms:
        html = search_web(name, term)
        investments = extract_investment_details(html)
        summary = summarize_investments(investments)
        summaries[name] = summary

scores = score_investments(summaries)
sorted_investors = sorted(scores.items(), key=lambda item: item[1], reverse=True)

print(sorted_investors)
### Contributing
- ** Contributions are welcome! Please feel free to submit a Pull Request.

### License
- ** This project is licensed under the MIT License. See the LICENSE file for details.
### Additional Files

- **requirements.txt**: Include this file to list the Python packages required for the project.

```txt
requests
beautifulsoup4
openai
