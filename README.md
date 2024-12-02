# EDA-Analysis-Asian-Growth-And-Development-using-Python
import kagglehub
import pandas as pd
import os

# Download latest version
dataset_dir = kagglehub.dataset_download("willianoliveiragibin/asian-growth-and-development")

# Find the CSV file within the downloaded directory
for filename in os.listdir(dataset_dir):
    if filename.endswith(".csv"):
        csv_file_path = os.path.join(dataset_dir, filename)
        break  # Stop searching once a CSV file is found

# Read the CSV file into a pandas DataFrame
asian_growth_and_development = pd.read_csv(csv_file_path)

asian_growth_and_development = pd.read_csv(csv_file_path)
asian_growth_and_development.head()

# menghitung korelasi antar pasangan variabel
asian_growth_and_development.select_dtypes(include=['number']).corr()

# menghitung korelasi antar pasangan variabel
# asian_growth_and_development.select_dtypes(include=['number']).corr() ['Mortality rate, infant (per 1,000 live births)]

correlation_with_mortality = asian_growth_and_development.select_dtypes(include=['number']).corr()['Mortality rate, infant (per 1,000 live births)']
correlation_with_mortality

# asian_growth_and_development.select_dtypes(include=['number']).corr() ['Mortality rate, infant (per 1,000 live births)] ['population, total']

correlation_mortality_population = asian_growth_and_development.select_dtypes(include=['number']).corr()['Mortality rate, infant (per 1,000 live births)']['Population, total']

print(f"Correlation between Mortality Rate and Total Population: {correlation_mortality_population}")

#Plotting

sns.scatterplot(x='Life expectancy at birth, total (years)', y='Mortality rate, infant (per 1,000 live births)', data=asian_growth_and_development)

sns.pairplot(asian_growth_and_development)

import seaborn as sns
import pandas as pd
import kagglehub
import os

# Download latest version
dataset_dir = kagglehub.dataset_download("willianoliveiragibin/asian-growth-and-development")

# Find the CSV file within the downloaded directory
for filename in os.listdir(dataset_dir):
    if filename.endswith(".csv"):
        csv_file_path = os.path.join(dataset_dir, filename)
        break  # Stop searching once a CSV file is found

# Read the CSV file into a pandas DataFrame
asian_growth_and_development = pd.read_csv(csv_file_path)

# Now you can use asian_growth_and_development in your plotting code
sns.histplot(asian_growth_and_development['GDP growth (annual %)'])


sns.scatterplot(
    data=asian_growth_and_development,
    x='Unemployment, total (% of total labor force) (modeled ILO estimate)',
    y='Unemployment, total (% of total labor force) (modeled ILO estimate)'
)

# menghitung korelasi dengan metode yang lain
asian_growth_and_development.select_dtypes(include=['number']).corr(method='spearman')

asian_growth_and_development.select_dtypes(include=['number']).corr(method='kendall')
