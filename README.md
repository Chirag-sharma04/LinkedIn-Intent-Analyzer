# LinkedIn Scraper and Analyzer

This Python script automates the process of scraping LinkedIn posts and their comments based on a specified keyword. It then analyzes the scraped content by comparing it to a predefined set of intent sentences using cosine similarity. The script extracts relevant information such as profile handles, profile links, post/comment content, timestamps, and the best-matched intent with similarity scores.

## Features

-   **LinkedIn Post Scraping:**
    -      Scrapes LinkedIn posts based on a provided keyword.
    -      Handles dynamic content loading and scrolling.
    -      Extracts post content, profile handles, profile links, timestamps, and post URLs.
    -      Avoids duplicate post entries.
-   **LinkedIn Comment Scraping:**
    -      Scrapes comments from each scraped LinkedIn post.
    -      Extracts comment content, profile handles, profile links, and timestamps.
    -      Handles "load more comments" functionality.
-   **Intent Analysis:**
    -      Calculates cosine similarity between scraped post/comment text and predefined intent sentences.
    -      Identifies the best-matched intent for each post/comment.
    -      Provides similarity scores for the matches.
-   **Data Export:**
    -      Saves scraped post data to `LinkedIn_posts_result.csv`.
    -      Saves scraped comment data to `LinkedIn_comments.csv`.
-   **Robust Error Handling:**
    -      Implements safe element finding and clicking to handle dynamic web pages.
    -      Includes multiple XPath options to adapt to LinkedIn's changing structure.
    -   Handles many possible exceptions, and continues to run.
-   **Anti-Detection Measures:**
    -   Uses `undetected_chromedriver` to bypass anti-bot detection.
    -   Rotates user-agents to mimic human behavior.
    -   Adds random delays to simulate human interaction.
-   **Timestamp Cleaning:**
    -   Cleans and standardizes timestamp formats.

## Prerequisites

-   Python 3.x
-   Required Python libraries:
    -   `pandas`
    -   `selenium`
    -   `undetected-chromedriver`
    -   `datetime`
    -   `pytz`
    -   `scikit-learn` (for cosine similarity, within cosine\_sim.py)
    -   `re`
    -   `random`
-   Ensure you have a `cosine_sim.py` file in the same directory, containing the `calculate_similarity_scores` function.
-   A Google Chrome browser installed.
-   A LinkedIn account with an active session in the specified Chrome profile.

## Installation

1.  Clone the repository or download the script.
2.  Install the required Python libraries:

    ```bash
    pip install pandas selenium undetected-chromedriver scikit-learn
    ```

3.  Ensure your `cosine_sim.py` file is present in the same directory.
4.  Modify the `setup_driver()` function in the script to point to your Chrome user data directory and profile.

    ```python
    chrome_options.add_argument(r'--user-data-dir=C:\Users\YOUR_USER\AppData\Local\Google\Chrome\User Data')
    chrome_options.add_argument(r'--profile-directory=YOUR_PROFILE')
    ```

    Replace `YOUR_USER` and `YOUR_PROFILE` with your actual Chrome user data directory and profile name.

## Usage

1.  Run the script:

    ```bash
    python your_script_name.py
    ```

2.  The script will scrape LinkedIn posts and comments based on the defined keyword ("Artificial Intelligence" by default) and save the results to `LinkedIn_posts_result.csv` and `LinkedIn_comments.csv`.

## Customization

-   **Keyword:** Change the `keyword` variable in the `main()` function to scrape posts related to a different topic.
-   **Number of Posts:** Adjust the `num_posts` variable in the `main()` function to control the number of posts to scrape.
-   **Intent Sentences:** Modify the `intent_data` list to change the intent sentences used for analysis.
-   **XPath Selectors:** If LinkedIn's HTML structure changes, update the XPath selectors in the `scrape_linkedin_posts()` and `scrape_linkedin_post_comments()` functions.
-   **Chrome Profile:** ensure the chrome profile is correct in setup_driver().

## Notes

-      This script is intended for educational and personal use.
-      Be mindful of LinkedIn's terms of service and avoid excessive scraping that may violate their policies.
-   The script relies on the structure of the LinkedIn webpage, which can change. Therefore, it may require maintenance to function correctly over time.
-   The `cosine_sim.py` file is assumed to be in the same directory. It should contain a function called `calculate_similarity_scores` that accepts a list of strings and a list of intent sentences and returns a NumPy array containing the cosine similarity scores.
-   This script uses `undetected_chromedriver` to reduce the risk of detection, but LinkedIn may still implement measures to block automated access.
