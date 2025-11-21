<img width="1243" height="735" alt="image" src="https://github.com/user-attachments/assets/d12a9f5e-1dc1-4daa-b9e9-61dc401a1862" />
<img width="1547" height="689" alt="image" src="https://github.com/user-attachments/assets/0fdcae53-5443-4b6c-8c2c-62685edb3afa" />


```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Create a sample DataFrame
data = pd.DataFrame({
    "column1": np.random.rand(50),  # 50 random values for column1
    "column2": np.random.rand(50) * 10  # 50 random values (multiplied by 10) for column2
})

# Display the first few rows
print(data.head())

# Create a scatter plot
plt.scatter(data["column1"], data["column2"])
plt.xlabel("Column 1")
plt.ylabel("Column 2")
plt.title("Scatter Plot")
plt.show()
```

<img width="945" height="613" alt="image" src="https://github.com/user-attachments/assets/5d87d5c1-2a33-48ec-bae6-d1b630c8f8d3" />

