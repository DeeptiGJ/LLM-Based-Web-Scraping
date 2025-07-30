# Earth911 Recycling Center Scraper

This Python script is designed to scrape recycling center information from the Earth911 website. It allows you to search for recycling facilities based on material type and zip code, filter by distance, and extract structured data about each facility, including its name, address, contact information, and categorized materials accepted.

## Features

1. Targeted Search: Search for recycling centers based on a specific material (e.g., "Electronics") and a U.S. zip code.

2. Distance Filtering: Filter search results to a specified radius (e.g., "100 miles").

3. Structured Data Extraction: Extracts business_name, street_address, phone, materials_category, and materials_accepted for each facility.

4. Material Categorization: Automatically maps raw materials found on the website to predefined broad Materials_Category (e.g., "Electronics", "Batteries") and specific Materials_Accepted items.

5. BOM Character Handling: Automatically cleans up invisible BOM (\ufeff) characters from extracted text.

6. Dynamic Pop-up Handling: Includes robust logic to detect and close pop-up overlays that may appear on the website.

## Prerequisites

Before running the script, ensure you have the following installed:

1. Python 3.x: Download from python.org.

2. pip: Python's package installer (usually comes with Python).

3. Google Chrome Browser: The script uses chromedriver, so Chrome needs to be installed.

4. ChromeDriver: A WebDriver for Chrome. You must download the version that matches your Chrome browser's version.

Download from: ChromeDriver Downloads

Place chromedriver in a directory that's in your system's PATH, or specify its path when initializing the WebDriver (e.g., webdriver.Chrome(executable_path='/path/to/chromedriver')). For simplicity, it's often placed in the same directory as the script, or in a PATH location.

## Installation

### Install required Python libraries:

Open your terminal or command prompt and run:

pip install selenium beautifulsoup4

### Set up ChromeDriver:

Download the appropriate chromedriver.exe (Windows) or chromedriver (macOS/Linux) for your Chrome browser version from the link above.

Place the chromedriver executable in a location accessible by your system's PATH, or in the same directory as your earth911_scraper.py script.

## Usage

To run the scraper, you will call the scrape_earth911 function with the desired material, zipcode, and distance.

## Result Parameters

The scrape function accepts the following parameters:

1. material (string, required): The specific material you are looking to recycle. Examples include 'Electronics', 'Batteries', 'Paint & Chemicals', etc.

2. zipcode (string, required): A 5-digit U.S. postal code where you want to search for recycling centers.

3. distance (integer, required): The maximum radius in miles for the search. Accepted values are 5, 10, 25, 50, or 100.

## Output Format

The script outputs a JSON array, where each object represents a recycling facility or program.

[

  {
  
    "business_name": "Green Earth Recyclers",
    
    "last_update_date": "2025-07-30",
    
    "street_address": "123 5th Ave, New York, NY 10001",
    
    "phone": "(212) 564-1600",
    
    "materials_category": ["Electronics", "Batteries"],
    
    "materials_accepted": ["Computers, Laptops, Tablets", "Cell Phones, Smartphones", "Lithium-ion Batteries"]
    
  }
  
]

## Material Categories and Mapping

The script uses an internal MATERIAL_MAPPING dictionary to categorize the diverse material names found on Earth911 into broader categories and a standardized list of accepted items.

The predefined Materials_Category types are:

"Electronics"

"Batteries"

"Paint & Chemicals"

"Medical Sharps"

"Textiles/Clothing"

"Other Important Materials"

Each category has a list of keywords and their corresponding detailed Materials_Accepted descriptions.

## Customization

You can customize the MATERIAL_MAPPING dictionary within the main file to refine how raw material names from Earth911 are mapped to desired categories and accepted items. 
