### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old":(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  visitors_count=len(count)
  print(f"The visitors on {group} age are")
  print(visitors)
  print("count=",len(visitors))
```
### Output:
<img width="477" height="690" alt="image" src="https://github.com/user-attachments/assets/53c1e90a-0862-4dba-9fbc-dcb605062ed3" />


### Visualization:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="997" height="687" alt="image" src="https://github.com/user-attachments/assets/d6d38a59-c6fd-4d38-8253-a96ffda3073d" />

### Program2
```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3
```

### Output:

<img width="316" height="1007" alt="image" src="https://github.com/user-attachments/assets/5115c5d3-788b-4d20-b44e-f90c7b505daa" />

### Visualization:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()
```
### Output:

<img width="1127" height="716" alt="image" src="https://github.com/user-attachments/assets/6c994443-2fc6-4079-b862-e23c717d5c18" />


### Result:
Thus, Cluster and Visitor Segmentation for Navigation patterns in Python is implemented successfully.
