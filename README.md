# Machine-learning-Data-Project

import pandas as pd
import numpy as np

def clean_data(input_file, output_file):
    # Load raw data
    df = pd.read_csv(S&P500.csv)

    # Handle missing values
    df['column_name'] = df['column_name'].fillna(df['column_name'].mean())  # Fill with mean for numerical columns
    df['column_name'] = df['column_name'].fillna(df['column_name'].mode()[0])  # Fill with mode for categorical columns

    # Remove duplicates
    df = df.drop_duplicates()

    # Convert data types
    df['date_column'] = pd.to_datetime(df['date_column'])
    df['categorical_column'] = df['categorical_column'].astype('category')

    # Remove unnecessary columns
    df = df.drop(columns=['unnecessary_column1', 'unnecessary_column2'])

    # Save cleaned data
    df.to_csv(output_file, index=False)
    print(f"Cleaned data saved to {output_file}")

if __name__ == "__main__":
    input_file = '../data/raw_data.csv'
    output_file = '../data/cleaned_data.csv'
    clean_data(input_file, output_file)
