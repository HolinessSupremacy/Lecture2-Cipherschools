# Lecture2-Cipherschools
#Lesson on Exploratory data analysis and DataScience workflow model

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Sample data: distance (km), delivery_time (minutes), traffic (0: low, 1: medium, 2: high), on_time (0: no, 1: yes)
data = {
    'distance': [5, 10, 2, 8, 7, 3, 1, 4, 6, 12, 5, 7, 9, 3, 2],
    'delivery_time': [30, 60, 15, 45, 50, 20, 10, 25, 35, 70, 40, 55, 65, 25, 15],
    'traffic': [1, 2, 0, 1, 2, 0, 0, 1, 2, 2, 1, 2, 2, 1, 0],
    'on_time': [1, 0, 1, 1, 0, 1, 1, 1, 0, 0, 1, 0, 0, 1, 1]
}

# Convert to DataFrame
df = pd.DataFrame(data)

# Display the first few rows of the DataFrame
print("First few rows of the dataset:")
print(df.head())

# Summary statistics
print("\nSummary statistics:")
print(df.describe())

# Check for missing values
print("\nMissing values in the dataset:")
print(df.isnull().sum())

# Data distribution plots
plt.figure(figsize=(10, 6))

# Histogram for distance
plt.subplot(2, 2, 1)
sns.histplot(df['distance'], kde=True, bins=10, color='blue')
plt.title('Distance Distribution')

# Histogram for delivery time
plt.subplot(2, 2, 2)
sns.histplot(df['delivery_time'], kde=True, bins=10, color='green')
plt.title('Delivery Time Distribution')

# Count plot for traffic
plt.subplot(2, 2, 3)
sns.countplot(x='traffic', data=df, palette='viridis')
plt.title('Traffic Condition Count')

# Count plot for on-time delivery
plt.subplot(2, 2, 4)
sns.countplot(x='on_time', data=df, palette='viridis')
plt.title('On-Time Delivery Count')

plt.tight_layout()
plt.show()

# Correlation matrix
print("\nCorrelation matrix:")
print(df.corr())

# Heatmap of the correlation matrix
plt.figure(figsize=(8, 6))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm', linewidths=0.5)
plt.title('Correlation Matrix Heatmap')
plt.show()

# Pairplot
sns.pairplot(df, hue='on_time', palette='viridis')
plt.show()

# Boxplot for delivery time by on-time delivery status
plt.figure(figsize=(8, 6))
sns.boxplot(x='on_time', y='delivery_time', data=df, palette='viridis')
plt.title('Delivery Time by On-Time Delivery Status')
plt.show()
