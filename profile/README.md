<br>

This hub hosts the repositories of a token classification modelling task in development.  Readers may interact with the latest model via a  <a href="https://greyhypotheses-detecting-eclectic.hf.space/" target="_blank">simple open interface</a>; note, training incomplete, i.e., stopped prematurely.

## Expected Structures

The `special` package reads-in the 


The tokenization class for the T5 architecture expects a **DatasetDict** of three partitions, i.e., keys: `train`, `validation`, `test`.  Each partition is a **datasets.arrow_dataset.Dataset**, and its structure is of the form

```
{'id': ['13487', '24698'], 'tokens': [['Salbutamol', ',', 'also', 'known', 'as', 'albuterol', 'and', 'marketed', 'as', 'Ventolin', 'among', 'other', 'brand', 'names', ',', 'is', 'a', 'medication', 'that', 'opens', 'up', 'the', 'medium', 'and', 'large', 'airways', 'in', 'the', 'lungs', '.'], ['Under', 'its', 'cultural', 'sponsorship', 'program', ',', 'Kärcher', 'has', 'supported', 'more', 'than', '90', 'projects', 'to', 'clean', 'internationally', 'prominent', 'buildings', 'such', 'as', 'the', 'National', 'Monument', 'in', 'Jakarta', '(', '2014', ')', ',', 'the', 'London', 'Eye', 'in', 'London', '(', '2013', ')', ',', 'the', 'Space', 'Needle', 'in', 'Seattle', '(', '2008', ')', ',', 'the', 'Presidents', '’', 'heads', 'at', 'the', 'Mount', 'Rushmore', 'National', 'Memorial', '(', '2005', ')', ',', 'the', 'Colossi', 'of', 'Memnon', 'in', 'Luxor', '(', '2003', ')', ',', 'the', 'Colonnades', 'on', 'St', 'Peter', '’', 's', 'Square', 'in', 'Rome', '(', '1998', ')', ',', 'the', 'Brandenburg', 'Gate', 'in', 'Berlin', '(', '1990', ')', 'the', 'Statue', 'of', 'Liberty', 'in', 'New', 'York', 'City', '(', '1985', ')', 'and', 'the', 'Statue', 'of', 'Christ', 'in', 'Rio', 'de', 'Janeiro', '(', '1980', ')', '.']], 'fine_ner_tags': [[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 6, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 2, 2, 2, 2, 0, 0, 0, 0, 0, 1, 1, 1, 0, 4, 0, 0, 0, 0, 0, 1, 0, 2, 2, 2, 2, 2, 0, 4, 0, 0, 0, 0, 0, 1, 1, 0, 4, 0, 0, 0, 0, 1, 1, 1, 0, 4, 4, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 4, 4, 4, 0, 0, 0, 0]]}
```


<br>
<br>

<br>
<br>

<br>
<br>

<br>
<br>

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
