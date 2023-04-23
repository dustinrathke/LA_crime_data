import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Load the data from the CSV file
data = pd.read_csv('https://data.lacity.org/api/views/2nrs-mtv8/rows.csv')

# Time Series Analysis
# Convert the 'date_occurred' column to a datetime data type
data['DATE OCC'] = pd.to_datetime(data['DATE OCC'])

# Set the 'date_occurred' column as the index of the dataframe
data.set_index('DATE OCC', inplace=True)

# Resample the data by day and count the number of calls for each day
data['daily_calls'] = data['DR_NO'].resample('D').count()

# Plot the daily call volume over time
plt.plot(daily_calls.index, daily_calls.values)
plt.title('LAPD Calls for Service')
plt.xlabel('Date')
plt.ylabel('Number of Calls')
plt.figure(figsize=(10,5))
#plt.xticks(daily_calls.index[::len(daily_calls)//100])
plt.show()

# Geographic Analysis
# Group the data by location and count the number of calls for each location
location_counts = data.groupby(['LAT', 'LON']).size().reset_index(name='count')

# Create a scatter plot of the call locations
plt.scatter(location_counts['LON'], location_counts['LAT'], c=location_counts['count'], cmap='viridis', alpha=0.5)
plt.title('LAPD Calls for Service by Location')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.colorbar(label='Number of Calls')
# Zoom out on the scatter plot
plt.xlim([-118.6, -118.1])
plt.ylim([33.6, 34.4])
plt.show()

# Sort the data by count in descending order and plot a bar chart
type_counts.sort_values('count', ascending=False, inplace=True)
plt.bar(type_counts['Crm Cd'], type_counts['count'])
plt.xticks(rotation=90)
plt.title('LAPD Calls for Service by Type')
plt.xlabel('Call Type')
plt.ylabel('Number of Calls')
plt.show()
