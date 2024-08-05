# GoogleMapsScraper_France

# README

## Overview

This project fetches details about places (hotels) within France using the Google Maps API and saves the results to an Excel file. It splits France's geographical area into a grid and queries the Google Maps API for each grid point to ensure comprehensive coverage. The results include place names, addresses, phone numbers, and websites.

## Prerequisites

Before you begin, ensure you have met the following requirements:
- Python 3.x installed on your local machine.
- Necessary Python packages installed (see below).
- A Google Maps API key.
- A GeoJSON file containing France's borders.

### Required Python Packages

You can install the required packages using pip:

```sh
pip install googlemaps openpyxl rich shapely
```

### Google Maps API Key

You need to have a valid Google Maps API key. You can obtain one by following the instructions at [Google Cloud Platform](https://cloud.google.com/maps-platform).

### GeoJSON File

You need a GeoJSON file containing the geographical borders of France. Ensure this file is accurate and correctly formatted.

## Setup

1. Clone the repository or download the script to your local machine.
2. Place your GeoJSON file in the project directory and update the `GEOJSON_FILE_PATH` variable in the script with the correct path.
3. Update the `API_KEY` variable in the script with your Google Maps API key.

## Usage

1. Run the script:

```sh
python script_name.py
```

2. The script will load the GeoJSON file, generate grid coordinates, and query the Google Maps API for each grid point to fetch details about hotels.
3. The results will be saved to an Excel file named `hotel_in_France.xlsx`.

### Important Variables

- `API_KEY`: Your Google Maps API key.
- `GEOJSON_FILE_PATH`: Path to your GeoJSON file containing France's borders.
- `NUM_GRIDS`: Number of grids to split the bounding box into.
- `MAX_REQUESTS_PER_DAY`: Maximum number of API requests allowed per day.
- `MAX_REQUESTS_PER_MINUTE`: Maximum number of API requests allowed per minute.
- `query`: Type of place to search for (e.g., "hotel").
- `radius`: Radius for the search around each grid point.

## Code Overview

### Importing Libraries

The script imports necessary libraries such as `googlemaps`, `time`, `openpyxl`, `rich`, `datetime`, `timedelta`, `shapely`, `json`, and `os`.

### Initializing Rich Console

A rich console is initialized for better terminal output.

```python
console = Console()
```

### Loading GeoJSON File

The script loads France borders from a GeoJSON file.

```python
GEOJSON_FILE_PATH = 'path_to_france_geojson.geojson'
```

### Setting Number of Grids

The script sets the number of grids to split the bounding box into.

```python
NUM_GRIDS = 10000
```

### Defining Maximum API Requests

The script defines the maximum number of API requests allowed per day and per minute.

```python
MAX_REQUESTS_PER_DAY = 500000
MAX_REQUESTS_PER_MINUTE = 2000
```

### Functions

#### `create_excel_file(data, filename)`

Creates an Excel file from the data.

#### `get_place_details(gmaps, place_id)`

Fetches details for a place ID.

#### `get_places(api_key, query, location, radius)`

Fetches places for a given location and radius.

#### `generate_grid_coordinates(borders, num_grids)`

Generates grid coordinates within the borders.

#### `save_and_prompt(data, filename)`

Saves the data to an Excel file and prompts the user to continue or stop.

### Main Process

The `main()` function initializes the process, generates grid coordinates, fetches data for each grid point, and saves the results to an Excel file.

```python
if __name__ == "__main__":
    main()
```

## Contributing

If you want to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.
