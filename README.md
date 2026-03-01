# GDP-Growth-Rate
GDP Growth Rate
Here is the annual GDP growth data of Bangladesh from 2000-2024, we can see a long-term uptrend with some short-term shocks. In the early 2000s, it was around size of about 4–5% which means a stable yet growing economy. Starting from 2005 the growth picked up rapidly above 6%, leading to a sustained strong expansion- spearheaded by exports, remittances and industrialization. While growth fell during the 2008 global financial crisis, the slowdown was modest and demonstrated resilience. Somewhere around 2019, the economy reached peak performance with growth rate lingering at almost 8%. In 2020, GDP growth declined significantly because of the COVID-19 pandemic. Nonetheless, GDP growth remained positive and recovered rapidly in 2021–2022. But growth fell again in 2023–2024, probably because of inflation, currency depreciation and tighter monetary conditions. The underlying data shows structural improvement over 20 years, even in the face of recent macroeconomic headwinds.
![Bangladesh Annual GDP Growth Rate](https://github.com/user-attachments/assets/db2a8a49-af4e-4756-a563-3c7137d8ad3f)

import wbdata
import pandas as pd
import datetime
import matplotlib.pyplot as plt

# 1. Define time period and indicator
data_date = (datetime.datetime(2000, 1, 1), datetime.datetime(2024, 1, 1))
indicator = {"NY.GDP.MKTP.KD.ZG": "GDP Growth (%)"}

# 2. Fetch data
df = wbdata.get_dataframe(indicator, country="BGD", date=data_date)
df = df.reset_index()

# 3. Clean Data: Ensure 'date' is a datetime object and sort it
df['date'] = pd.to_datetime(df['date'])
df = df.sort_values("date")

# 4. Plotting the data
plt.figure(figsize=(12, 6))
plt.plot(df['date'], df['GDP Growth (%)'], marker='o', linestyle='-', color='teal', linewidth=2)

# Adding labels and styling
plt.title('Bangladesh Annual GDP Growth Rate (2000-2024)', fontsize=14, fontweight='bold')
plt.xlabel('Year', fontsize=12)
plt.ylabel('Growth Rate (%)', fontsize=12)
plt.grid(True, linestyle='--', alpha=0.7)
plt.axhline(0, color='black', linewidth=1) # Adds a baseline at 0%

# Show the plot
plt.tight_layout()
plt.show()
