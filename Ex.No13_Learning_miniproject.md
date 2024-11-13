## Ex.No: 13 Learning – Use Supervised Learning  
## DATE: 24/10/2024                                                                            
## REGISTER NUMBER : 212222060281
## AIM: 
To create a ML model using python to predict PCOS using Randomforest classifier.
##  Algorithm:
1. Load and Prepare Data: Load the CSV file, check for missing values, and impute them using the mean strategy.<br>

2. Set Features and Target: Define X (features) and y (target, indicating PCOS diagnosis).<br>

3. Split and Standardize: Split data into training and test sets; standardize the feature values using StandardScaler.<br>

4. Train the Model: Use a RandomForestClassifier to train the model on the training set.<br>

5. Evaluate: Predict on the test set and evaluate the model's accuracy.<br>

6. Chatbot Interface: Define a function to collect user inputs for each feature, including special handling for blood group values.<br>

7. Predict and Display Result: Preprocess user input, make a prediction, and display the result to the user.<br>

## Program:
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report

# Load the dataset
data_path = '/content/CLEAN- PCOS SURVEY SPREADSHEET.csv'
df = pd.read_csv(data_path)

# Display the first few rows of the dataset
df.head()

# Check for missing values
df.isnull().sum()

# Fill missing values using SimpleImputer
imputer = SimpleImputer(strategy='mean')
df_imputed = pd.DataFrame(imputer.fit_transform(df), columns=df.columns)

# Encode categorical
# Assuming 'PCOS' is the target column (replace with actual column name if different)
target_column = 'Have you been diagnosed with PCOS/PCOD?'  # You may need to change this based on the actual name

# Select features (excluding the target)
X = df_imputed.drop(columns=[target_column])
y = df_imputed[target_column]

# Split the data into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Standardize the feature values
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Display the shape of the dataset to confirm
X_train_scaled.shape, X_test_scaled.shape

# Initialize and train the Random Forest model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train_scaled, y_train)

# Make predictions on the test set
y_pred = model.predict(X_test_scaled)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
print(f"Model Accuracy: {accuracy}")
print(classification_report(y_test, y_pred))

# Chatbot to take user input
def pcos_chatbot():
    print("Welcome to the PCOS detection chatbot!")
    print("Please answer the following questions:")

    # Blood group mapping
    blood_group_mapping = {
        'A+': 11, 'A-': 12,
        'B+': 13, 'B-': 14,
        'O+': 15, 'O-': 16,
        'AB+': 17, 'AB-': 18
    }

    user_data = []

    for feature in X.columns:
        if 'blood group' in feature.lower():
            # Special case for blood group input
            blood_group = input("Enter your blood group (e.g., A+, O-): ").upper()
            if blood_group in blood_group_mapping:
                value = blood_group_mapping[blood_group]
            else:
                print("Invalid blood group entered. Please try again.")
                return
        else:
            # General input for other features
            value = float(input(f"Enter value for {feature}: "))

        user_data.append(value)

    # Preprocess the input data
    user_data_scaled = scaler.transform([user_data])

    # Make prediction
    prediction = model.predict(user_data_scaled)

    if prediction == 1:
        print("The chatbot predicts that you might have PCOS. Please consult a doctor for further evaluation.")
    else:
        print("The chatbot predicts that you likely do not have PCOS. However, consult a doctor if you have concerns.")

# Run the chatbot
pcos_chatbot()
```

## Output:
![Screenshot 2024-10-12 221053](https://github.com/user-attachments/assets/703aa47b-b6aa-4b75-901b-ffe047a67c73)
![image](https://github.com/user-attachments/assets/8f1b6696-3acf-4156-9541-c1a6a7bfba5f)


## Result:
The ML model to predict PCOS is created successfully.
