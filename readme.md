## JDT's Google Merchant Center Feed Status Setup Guide

## Dependencies
The following libraries are required to run the Google Merchant Center Feed Status Reporter:
- [requests](https://pypi.org/project/requests/)
- [google-api-python-client](https://pypi.org/project/google-api-python-client/)
- [google_auth_oauthlib](https://pypi.org/project/google-auth-oauthlib/)
- [google-auth-httplib2](https://pypi.org/project/google-auth-httplib2/)
- [google-auth](https://pypi.org/project/google-auth/)
- [oauth2client](https://pypi.org/project/oauth2client/)
- [tabulate](https://pypi.org/project/tabulate/)

## Set Up
To set up the Google Merchant Center Feed Status Reporter, complete the following steps:
1. Clone the 'google/gmc-feed_status' sample code from [GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).
2. Create a folder for the authentication files within the '/Google/GMC-feed_status/content', titled 'authfiles'.
    - e.g.: <b>your-home-directory/Google/GMC-feed_status/content/authfiles/</b>
3. Setup authentication files:
    - Go to [Google Merchant Center](https://merchants.google.com/) and obtain the API Key:
        - In Merchant Center, in the Settings menu, select Content API.
        - Click Authentication.
        - Click <b>'+'</b> CREATE API KEY. 
    - If prompted, read and accept the terms of service agreements. The new key downloads automatically.
        - Rename the downloaded credentials file to service-account.json.
    - Note: This filename is defined in the _constants.py file, which is located in '/Google/GMC-feed_status/content/' folder.'
        - Move the service-account.json file to 'your-home-directory/Google/GMC-feed_status/content/authfiles/' folder.
4. Setup mechant-info.json:
    - In 'your-home-directory/Google/GMC-feed_status/content/authfiles/'', folder create an empty merchant-info.json file.
    - In merchant-info.json, add the following text:
        - [
            {"propName": "your_acct_name", "merchantId": "acct_merchant_id"},
        ]
        - Replace <b>'your_acct_name'</b> with your account name and <b>'merchant_id'</b> with your merchant ID.
        - 'your_acct_name' is arbitrarily named and is based on your preference for display and identification.
        - 'merchant_id' is the Merchant Center merchant ID.
        - If you have multiple merchant accounts, add additional entries in the array in the same format, separated by commas:
        - [
            {"propName": "your_acct_name", "merchantId": "acct_merchant_id"},
            {"propName": "your_acct_name", "merchantId": "acct_merchant_id"},
            ..... more as needed
            ]
    - Save and close the file.
5. Run the sample code: 'python you-home-directory/Google/GMC-feed_status/main.py' (or whatever folder hierarchy you setup) and follow the prompts.
    - Automated reports - Use the following arguments for automated actions:
        - '--auto list-errors' = Run a status check and report all failed feed fetch attempts and item errors
            - ex: 'python you-home-directory/Google/GMC-feed_status/main.py --auto list-errors' 
        - '--auto display-all' = Output all feed data from all properties for review on screen
            - ex: 'python you-home-directory/Google/GMC-feed_status/main.py --auto display-all'
        - '--auto save-file' = Retrieve all properties feed data and save to CSV file (requires additional '--file_name arg')
            - ex: 'python you-home-directory/Google/GMC-feed_status/main.py --auto save-file --file_name feedreport' 
            - NOTE: Only enter the preferred name of the file, not the extension; the file will already be appended and saved as CSV file.
        - Use the '-h' or '--help' argument instead to review this list of automated options.