<h2>I) Discovery Part</h2>

We conducted a **sentiment analysis** using two YouTube videos discussing **Elon Musk**, a highly polarizing figure. His management, public statements, and political views spark strong reactions.  

Given this polarization, we selected two videos with **contrasting comment sections**:  
- **"Elon Musk: War, AI, Aliens, Politics..."** (Podcast)  
- **"Jon Stewart on the Trump Inauguration"** (TV segment mentioning Musk)  

<h3>YouTube's Role</h3>

With **2.5 billion users** and **1 billion hours watched daily**, YouTube shapes public opinion. Its **comment section** serves as a reflection of audience sentiment but can also amplify biases.  

<h3>Research Questions</h3>

- How well does **sentiment analysis** capture public perception of Elon Musk?  
- How do **YouTube comment sections** reflect polarized opinions?  

<br>

<h2>II) Data Preparation</h2>

We selected two videos with **23,000+ comments** and extracted the data using **Octoparse**.  

Key steps:  
- Removed unnecessary data (links, non-Latin characters)  
- Standardized missing values  
- Exported as an **Excel file**  
- Used **Google Colab & R** for cleaning and analysis  

<br>

<h2>III) Model Planning & Building</h2>

### 1. Dataset Overview  

- **Total comments**: 1,453 (676 podcast, 777 TV segment)  
- **Attributes**: comment, user, timestamp, likes, responses  
- **Languages**: Mostly English  

### 2. Clustering Model  

- Tokenized words and built a **document-term matrix**  
- Created a **distance matrix** and clustered data  
- **Findings**: Comments use similar, generic vocabulary, limiting clustering effectiveness  

### 3. Sentiment Analysis  

Using the **syuzhet** package, we:  
- Calculated sentiment scores  
- Classified emotions via **NRC analysis**  
- Grouped emotions into **positive** (joy, trust, anticipation) and **negative** (anger, fear, sadness) categories  

**Results**:  
- Comments were **twice as positive as negative**  
- Dominant emotions: **trust, joy, anticipation, and fear**  

<br>

<h2>IV) Communicating Results</h2>

### 1. Elon Musk Case  

- **Word analysis**: Comments focus on **emotions & hyperbole** (e.g., "love," "never," "always").  
- **Sentiment findings**: Community polarization is based on **trust vs. fear** of Musk.  

### 2. General Applicability  

- **Clustering is ineffective** due to repetitive vocabulary.  
- **Sentiment analysis works well**, as comments often express exaggerated emotions.  
- **Emotion analysis** reveals deeper insights into **public perception and polarization**.  

<h3>Future Considerations</h3>

- **Deep Learning models** could improve sentiment analysis by understanding **context and negation** (e.g., "don't like" misclassified).  
- However, this could introduce a **black-box effect**, reducing interpretability.  

This project highlights the **potential and limitations of sentiment analysis** in understanding public discourse on social media.  
