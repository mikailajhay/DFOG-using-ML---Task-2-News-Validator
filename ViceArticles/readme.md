# ****Vice Articles****
## **_Overview_**
In order to perform initial cleaning and validation of the data to assure quality and reliable information, a Python script was used to validate the 10,071 articles scraped from vice.com's website. 

## _**Features**_
### **Removed**
The rows which contains the following were taken out of the dataset:
- **Missing values** (NA/NaN)
- **Duplicate values** (an exception to this are the articles entitled "The VICE Morning Bulletin" since it is a part of the website's daily segment and it contains different content written by their staff)
- **Some content of articles** (those only whose number of words are less than 50)
### **Added**
- **"word count" column**
  - This column was added to be able to track down the number of words that every content of the article contains.
  - The implementation of this column made it possible to check articles that contain less than 50 words and omit them since they are too short to be considered as a news data.

## _**Conclusion**_
After conducting the fundamental data cleaning procedures mentioned above, the information on the dataset provided was reduced from 10,071 data to 10,031 data. Afterwards, a new CSV file was generated and saved (`df.to_csv('vice_articles_validated_v1.csv', index=False)`).
