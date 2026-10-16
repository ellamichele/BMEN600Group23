# BMEN600Group23

**RESEARCH QUESTION:**

   How accurately can gene expression in one human brain region predict expression in another in unseen GTEx donors, and how does        predictive performance vary across region pairs?

   
**Dataset:** 
   
   https://gtexportal.org/home/downloads/adult-gtex/bulk_tissue_expression
   
   To access the data used, click the link and scroll down to 'gene reads by tissue', staying within the V11 shell. Data used are        tissues from brain regions excluding the brainstem.
   
   2 Zip folders exist in the 'Releases' tab, containing metadata and our dataset. Files in the main branch include: the midterm         research plan finished pdf, our .ipynb google colab file containing all code, and the read me. 

**Software and Setup Instructions**

All analyses were implemented in Python 3 using Google Colab. NumPy and pandas were used for numerical calculations, RNA-seq data     preprocessing, donor matching, and data organization. Machine learning models were developed using scikit-learn, including Ridge      regression, StandardScaler, and train_test_split for model training, normalization, and donor-level evaluation. Matplotlib was        used to generate visualizations of dataset characteristics, prediction performance, and bootstrap confidence intervals. The           Requests package was used to retrieve GTEx V11 data from GitHub, while Python's standard libraries supported file management,         compressed-data extraction, and reproducibility documentation.
