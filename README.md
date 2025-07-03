# Visualized-GIS-Cameroon-Geomaterials-with-Cultural-Heritage-Activities-and-Locations
Visualized GIS Cameroon Geomaterials with Cultural Heritage Activities and Locations
import folium

# Step 1: Define coordinates (latitude, longitude) for heritage locations
location_coords = {
    "Batouri": (4.43, 14.37),
    "Mobilong": (3.52, 15.05),
    "Nkamouna": (3.87, 14.83),
    "Figuil": (9.73, 13.95),
    "Poli": (8.48, 12.23),
    "Mayo-Darlé": (6.53, 12.68),
    "Dehane": (3.67, 10.12),
    "Limbe": (4.02, 9.21),
    "Western Highlands": (5.92, 10.38)
}

# Optional: Cultural descriptions (can be expanded into popups)
location_info = {
    "Batouri": "Gbaya/Baka ancestral rituals, sacred forest zones.",
    "Mobilong": "Diamond zone with Baka pygmy heritage.",
    "Nkamouna": "Forest rituals, wood carving, traditional medicine.",
    "Figuil": "Pottery and Fulani Islamic traditions.",
    "Poli": "Doayo people, ancestral mountain caves.",
    "Mayo-Darlé": "Tin mining heritage, Mambila culture.",
    "Dehane": "Riverine rituals, sacred mangrove forests.",
    "Limbe": "Bimbia slave trade site, colonial gardens.",
    "Western Highlands": "Royal palaces, museums, Ngumba initiation rituals."
}

# Step 2: Create a folium map centered on Cameroon
cameroon_map = folium.Map(location=[6.0, 12.0], zoom_start=6, tiles='OpenStreetMap')

# Step 3: Add markers for each location with description popups
for location, coords in location_coords.items():
    popup_text = f"<b>{location}</b><br>{location_info.get(location, '')}"
    folium.Marker(
        location=coords,
        popup=folium.Popup(popup_text, max_width=300),
        icon=folium.Icon(color='red', icon='info-sign')
    ).add_to(cameroon_map)

# Step 4: Display the map (works in Jupyter/Colab)
cameroon_map
