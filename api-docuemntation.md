# MSC GeoMet - GeoMet-OGC-API Documentation

---
This documentation provides an overview of how to use the MSC GeoMet - GeoMet-OGC-API with urllib in Python.

Base URL: https://api.weather.gc.ca/

Key Endpoints:

- /collections: List available data collections
- /collections/{collectionId}: Get metadata for a specific collection
- /collections/{collectionId}/items: Get items from a collection
- /collections/{collectionId}/items/{featureId}: Get a specific item from a collection

Common Query Parameters:

- f: Output format (json, html, jsonld, csv)
- lang: Language (en-CA, fr-CA)

Example Usage:

import urllib.request
import json

# Get list of collections

url = "https://api.weather.gc.ca/collections?f=json"
with urllib.request.urlopen(url) as response:
collections = json.loads(response.read())

# Get items from a collection

collection_id = "climate-daily"
url = f"https://api.weather.gc.ca/collections/{collection_id}/items?f=json"
with urllib.request.urlopen(url) as response:
items = json.loads(response.read())

# Get a specific item

feature_id = "123456"  
url = f"https://api.weather.gc.ca/collections/{collection_id}/items/{feature_id}?f=json"
with urllib.request.urlopen(url) as response:
item = json.loads(response.read())

# Handle errors

try:
urllib.request.urlopen(url)
except urllib.error.HTTPError as e:
print(f"HTTP Error {e.code}: {e.reason}")
except urllib.error.URLError as e:
print(f"URL Error: {e.reason}")

Key Collections:

- climate-daily: Daily climate observations
- climate-monthly: Monthly climate summaries
- hydrometric-daily-mean: Daily mean water levels/flows
- weather:rdpa:10km:24f: 24-hour precipitation analysis

For more details on available collections and parameters, refer to the full API documentation.
"""
