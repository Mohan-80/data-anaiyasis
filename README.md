# data-anaiyasis
#importing Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

#step1:losd the Dataset
ur1="https://archive.ics.uci.edu/m1/machine-learning-database/00320/student.zip"
dataset_path="student-mat.csv"

#Download and load the dataset
import urllib.request
import zipfile

#Dowmload the dataset
urllib.request.urlretrieve(ur1,"student.zip")

#Extract the dataset
with zipfile.ZipFile("student.zip","r") as zip_ref:
    zip_ref.extractall(".")

#Load the data into a DataFrame
data=pd.read_csv("strudent_mat.csv",sep=";")
print("Data loaded successfully!")

#step2:Data Exploration
print(Data.head())
print("\n Dataset Info:")
print(data.info())

#step3:Data Clearing
#Check for missing value
print("\n missing Values:")
print(data.isnull().sum())

#Remove duplicates
data=data.drop_duplicates()

#step4: Data Analysis
#Question 1:what is average score in math(G3)?
average_score=data['G3'].mean()
print(f"\n Average Math Score(G3): {average_score:.2f}")

#Question 2: How many students above 15 in their final grade(G3)?
student_above_15=len(data[data['G3']>15])
print(f"Number of student scoring above 15: {student_above_15}")

#Question 3:is there a correction between study time and final grade?
correction=data['studytime'].corr(data['G3'])
print(f"Correlation between study time and final grade: {correlation:.2f}")

#Quet=stion 4:which gender has a higher average final grade?
average_grade_by_gender=data.groupby('sex')['G3'].mean()
print("\n Average Final Grade by Gender:")
print(average_grade_by_gender)


#step 5:Data Visualation
#Histogram of final grades
plt.figure(figsize=(8,5))
plt.hist(data['G3'], bins=10, color='skyblue',edgecolor='black')
plt.title("Distribution of final Grades(G3)")
plt.xlabel("Final Grades(G3)")
plt,ylabel("Frequency")
plt.show()

#Scater plot of study time vs. final grade
plt.figure(figsize=(8,5))
sns.scatterplot(data=data, x='studytime',y='G3', hue='sex')
plt.title("average Final vs Final Grade")
plt.ylabel("Avrage Final Grade")
plt.xlabel("Gender")
plt.xticks(rotation=0)
plt.show()

#Bar chart of average scores by gender
plt.figure(figsize=(8,5))
avrage_grade_by_gender.plot(kind='bar',color=['blue','pink'])
plt.title("Average Final Grade by Gender")
plt.ylabel("Average Final Grade")
plt.xlabel("Gender")
plt.xticks(rotation=0)
plt.show()
