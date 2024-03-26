# ExcelMerger
Merge Excel sheets 
import pandas as pd
import glob

def merge_excel_sheets(output_file='merged.xlsx'):
    # Get all Excel files in the current directory
    excel_files = glob.glob('*.xlsx')

    # Read and append each sheet
    merged_df = pd.DataFrame()
    for file in excel_files:
        df = pd.read_excel(file, engine='openpyxl')
        merged_df = merged_df.append(df, ignore_index=True)

    # Write the merged DataFrame to a new Excel file
    merged_df.to_excel(output_file, index=False, engine='openpyxl')
    print(f'Merged Excel sheets saved to {output_file}')

if __name__ == "__main__":
    merge_excel_sheets()
