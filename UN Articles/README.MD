# ****UN Articles****
## **_Overview_**
By utilizing a Python script, the dataset that contains 70,489 articles which were scraped from the UN website were initially cleaned and checked to ensure the data was legitimate and accurate.

## _**Features**_
### **Removed**
The rows which contains the following were taken out of the dataset:
- **Missing values** (except for author_link considering that there are more than 70,000 articles that doesn’t contain this): `df = df.dropna(subset = ['author', 'article_content', 'content_tags', 'content_tags_link']).reset_index(drop=True)`
- **Duplicate values**: `df = df.drop_duplicates(subset=['title'], keep='first').reset_index(drop=True)`
- **Articles whose content is less than 100 words**: `df.drop(df[df['word count'] < 100].index, inplace=True)`
### **Added**
- **"word count" column**
  - `df['word count'] = df['article_content'].str.split().str.len()`
  - This column was added to keep track of how many words each section of the article includes.
  - With the addition of this column, it is now possible to review articles with fewer than 100 words and remove them since they cannot be regarded as news data considering their length.
### **Observation**
There are several articles that was removed from the dataset (more than half) considering the enormous number of articles without authors.

## _**Conclusion**_
Following the essential data cleaning steps described above, the number of articles in the given dataset was decreased from 70,489 articles to 32,741 articles. Subsequently, a new CSV file was created then saved (`(df.to_csv('un_articles_validated_v1.csv', index=False)`).
