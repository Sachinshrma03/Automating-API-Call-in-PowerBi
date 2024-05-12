# Toll Rates Automation with Power Query

This repository contains a Power Query script that automates the process of fetching toll rates for various routes using the TollGuru API. The script takes a table with latitude and longitude coordinates as input and adds a new column with the minimum toll cost for each route.

## Prerequisites

- Microsoft Power BI Desktop or Microsoft Excel with Power Query enabled

## Getting Started

1. Clone or download the repository to your local machine.
2. Open Microsoft Power BI Desktop or Microsoft Excel.
3. In the Power Query Editor, navigate to the folder containing the script file (`Power Query for Automating the call.txt`).
4. Load the script into the Power Query Editor.

## Usage

1. Replace the `#"Sample-data"` line in the script with the name of your actual table.
2. Update the `"x-api-key"` value in the `headers` list with your TollGuru API key.
3. Execute the script in the Power Query Editor.

The script will perform the following steps:

1. Define a `MakeAPICall` function that constructs the API request URL, headers, and request body based on the provided latitude and longitude coordinates.
2. Define an `ExtractData` function that extracts the minimum toll cost for each route from the API response and adds it as a new column to the input table.
3. Load the input table specified by the `source` variable.
4. Transform each row of the input table using the `ExtractData` function and create a new table with the added "minimumTollCost" column.

## Script Breakdown

### `MakeAPICall` Function

This function takes four parameters: `lat1`, `long1`, `lat2`, and `long2`, representing the latitude and longitude coordinates of the origin and destination points, respectively. It constructs the API request URL, headers, and request body, and sends a POST request to the TollGuru API. The function returns the API response as a JSON document.

### `ExtractData` Function

This function takes a row from the input table as its parameter. It extracts the latitude and longitude coordinates from the row and calls the `MakeAPICall` function with these coordinates. The function then parses the API response and retrieves the minimum toll cost for the route. Finally, it adds the minimum toll cost as a new field to the input row and returns the updated row.

### Main Script

The main script performs the following tasks:

1. Defines the `MakeAPICall` and `ExtractData` functions.
2. Loads the input table specified by the `source` variable.
3. Transforms each row of the input table using the `ExtractData` function and creates a new table with the added "minimumTollCost" column.

## Note

Please note that the script assumes that the input table has columns named "Latitude", "Longitude", "End_Lat", and "End_Long". If your table has different column names, you will need to modify the script accordingly.

## Contributing

Contributions to this repository are welcome. If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
