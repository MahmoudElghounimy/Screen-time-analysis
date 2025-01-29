

### **Explanation of the Code:**

### **1. Importing Libraries**

```python
import pandas as pd
import numpy as np
import plotly.express as px
import plotly.graph_objects as go
```

- **`pandas`**: Used for data manipulation and reading the CSV file.
- **`numpy`**: Though imported, it is not explicitly used in this part of the code. It might be useful for numerical operations later.
- **`plotly.express`** and **`plotly.graph_objects`**: Both are used for creating interactive plots. **Plotly Express** provides high-level functions for quick plotting, while **Plotly Graph Objects** offers more flexibility for complex visualizations.

### **2. Loading the Dataset**

```python
data = pd.read_csv("Screentime-App-Details.csv")
```

- The dataset is loaded using **`pandas`** `read_csv()` function. It is assumed that this CSV contains details about app usage, notifications, and times opened.

```python
print(data.head())
```

- This line prints the first 5 rows of the dataset to give an overview of its structure and data.

### **3. Checking for Missing Values**

```python
data.isnull().sum()
```

- This line checks for missing values in the dataset by using **`isnull()`** to identify null values and **`sum()`** to count the number of null values per column. It helps in identifying whether any columns have missing data that needs to be handled.

### **4. Descriptive Statistics**

```python
print(data.describe())
```

- **`describe()`** provides statistical summaries for the numerical columns in the dataset, including metrics like mean, standard deviation, minimum, and maximum values.

### **5. Creating Visualizations with Plotly Express**

#### **Bar Chart for App Usage Over Time**

```python
figure = px.bar(data_frame=data,
                x="Date",
                y="Usage",
                color="App",
                title="Usage")
figure.show()
```

- This creates a bar chart using **Plotly Express** to visualize the usage of different apps over time (`Date` vs `Usage`). The **`color="App"`** argument adds color coding for each app, making it easier to distinguish between apps.

#### **Bar Chart for Notifications Over Time**

```python
figure = px.bar(data_frame=data ,
                x="Date",
                y="Notifications",
                color="App",
                title="Notifications ")
figure.show()
```

- Similar to the previous chart, this bar chart visualizes the number of **notifications** for each app over time. Again, **`color="App"`** groups the bars by app.

#### **Bar Chart for Times Opened Over Time**

```python
figure = px.bar(data_frame=data ,
                x="Date",
                y="Times opened",
                color="App",
                title="Times Opened ")
figure.show()
```

- This creates a bar chart visualizing the number of times each app was opened over time. It provides insights into app usage frequency.

#### **Scatter Plot: Relationship Between Notifications and Usage**

```python
figure = px.scatter(data_frame=data,
                    x="Notifications",
                    y="Usage",
                    size="Notifications",
                    trendline="ols",
                    title="Relationship Between Number of Notifications and Usage")
figure.show()
```

- This scatter plot visualizes the relationship between the number of **notifications** and **usage** of apps. The `size="Notifications"` argument scales the points based on the number of notifications, making it visually apparent which apps have more notifications.
- **`trendline="ols"`** adds a linear regression (OLS) trendline to show the relationship between notifications and usage more clearly.

