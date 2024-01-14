import pandas as pd
import matplotlib.pyplot as plt
from google.colab import files
uploaded = files.upload()

df = pd.read_excel('sec.xlsx')
# Save it as a CSV file
df.to_csv('sec.csv', index=False)
# Loading the data from the CSV file
data = pd.read_csv("sec.csv")


# (i) Finding the product with the highest total revenue for the quarter
highest_revenue_product = data[data['Total Revenue'] == data['Total Revenue'].max()]['Product Name'].values[0]
print(highest_revenue_product)
# (ii) Identifying products that consistently performed well throughout all three months
consistent_performers = data.groupby('Product Name').filter(lambda x: len(x) == 3)
if not consistent_performers.empty:
    print("Products that consistently performed well throughout all three months:")
    print(consistent_performers)
else:
    print("No products consistently performed well throughout all three months.")

# (iii) Calculating the correlation between price per unit and total revenue
correlation = data['Price Per Unit'].corr(data['Total Revenue'])
print("The correlation between price per unit and total revenue was:", correlation)



# (iv) Calculating the total revenue for the entire quarter
total_revenue_quarter = data['Total Revenue'].sum()
print("Total revenue for the entire quarter was:", total_revenue_quarter)

# (v) Visualizing the distribution of total revenue among products for the quarter
print("Visualizing the distribution of total revenue among products for the quarter in a pie chart")

# Visualizing the distribution of total revenue among products for the quarter in a bar graph
print("Visualizing the distribution of total revenue among products for the quarter in a bar graph")

plt.figure(figsize=(12, 6))
plt.bar(total_revenue_per_product.index, total_revenue_per_product.values)
plt.xlabel('Product Name')
plt.ylabel('Total Revenue')
plt.title('Total Revenue by product for the Quarter')
plt.xticks(rotation=45, ha="right")
plt.show()
No file chosen Upload widget is only available when the cell has been executed in the current browser session. Please rerun this cell to enable.
Saving sec.xlsx to sec.xlsx
product 2
Products that consistently performed well throughout all three months:
  Product Name  Units Sold  Price Per Unit  Total Revenue
0    product 1          50             200          10000
1    product 1          80             150          12000
2    product 1         100             150          15000
3    product 2          60             250          15000
4    product 2         150             300          45000
5    product 2          30             257           7710
6    product 3          50             248          12400
7    product 3          90             126          11340
8    product 3         130             138          17940
The correlation between price per unit and total revenue was: 0.4699345984138746
Total revenue for the entire quarter was: 146390
Visualizing the distribution of total revenue among products for the quarter in a pie chart
Visualizing the distribution of total revenue among products for the quarter in a bar graph

Data Import and Export:

I made use of Python's powerful data manipulation and analysis library, Pandas, by importing it with the alias pd. Pandas is essential for working with structured data.

I also brought in Matplotlib, another important library, using import matplotlib.pyplot as plt. Matplotlib is my go-to tool for creating various data visualizations.

Given that I'm working in the Google Colab environment, I used from google.colab import files to enable the uploading of files.

To kick things off, I utilized uploaded = files.upload() to allow the upload of a file, in this case, an Excel file named 'sec.xlsx.'

Data Loading and Export:

To make the data more accessible and portable, I loaded it into a Pandas DataFrame with df = pd.read_excel('sec.xlsx').

Then, to ensure easier data sharing and manipulation in different formats, I saved this DataFrame as a CSV file. I did this by using `df.to_csv('sec.csv', index=False).

Data Analysis:

(i) Finding the product with the highest total revenue for the quarter:

For this task, I needed to find the product that raked in the highest total revenue over the quarter. I accomplished this by filtering the DataFrame. Specifically, I used highest_revenue_product = data[data['Total Revenue'] == data['Total Revenue'].max()]['Product Name'].values[0] to identify this product.

(ii) Identifying products that consistently performed well throughout all three months:

To determine which products consistently performed well throughout all three months, I grouped the data by product name and applied a filter. The code snippet consistent_performers = data.groupby('Product Name').filter(lambda x: len(x) == 3) helped me achieve this. If any such products were found, I printed them. Otherwise, I printed a message indicating that no such products were identified.

(iii) Calculating the correlation between price per unit and total revenue:

To gain insights into the relationship between the price per unit and total revenue, I calculated the correlation coefficient. This was accomplished using the code correlation = data['Price Per Unit'].corr(data['Total Revenue']).

(iv) Calculating the total revenue for the entire quarter:

I computed the total revenue for the entire quarter by summing up the 'Total Revenue' column. The code for this task was total_revenue_quarter = data['Total Revenue'].sum().

At the end of the code, I created a bar graph to visualize the total revenue for each product. I adjusted the figure size, labels, title, and rotation for product names on the x-axis. Finally, I displayed the bar graph using plt.show(
