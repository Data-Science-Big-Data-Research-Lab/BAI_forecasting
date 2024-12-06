# Dataset Handling Instructions

Due to the large size of some dataset files, we have had to split them into smaller parts to comply with GitHub's file size limits. These split files are stored in the folder:

Datasets/RCPMerged/Datasets_splitted


To use the datasets in their original form, you need to merge the split files. Below, we explain how to do this step by step.

---

## **Steps to Merge Split Files**

1. Open your terminal and navigate to the main folder containing the datasets:

   cd Datasets/RCPMerged

2. Run the following command to merge the parts into their original files:



       for file in Datasets_splitted/*_part_1; do
   
           original_file=$(basename "$file" _part_1)
      
           cat Datasets_splitted/"$original_file"_part_* > "$original_file"
      
           echo "Merged $original_file"
         done
    

## Explanation of the Command
* The script finds all files in Datasets_splitted/ ending with _part_1.
* For each split dataset, it combines (cat) all parts (_part_1, _part_2, etc.) into a single file with the original name.
* The final merged files will appear directly in the Datasets/RCPMerged folder.

3. Verify that the files have been merged successfully. You can list the contents of the folder with:

    ls -lh Datasets/RCPMerged

## Important
* Ensure that you have write permissions in the Datasets/RCPMerged folder.
* The merging process will overwrite existing files with the same name in the Datasets/RCPMerged directory. If you want to keep the original files, back them up before running the merge script.
