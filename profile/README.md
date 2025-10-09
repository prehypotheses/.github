<br>

This hub hosts the repositories of a token classification modelling task in development.  Readers may interact with the latest model via a  <a href="https://greyhypotheses-detecting-eclectic.hf.space/" target="_blank">simple open interface</a>; note, training incomplete, i.e., stopped prematurely.

<br>

## Expected Structures

The raw/original Supervised Batch of FEW-NERD is a **datasets.dataset_dict.DatasetDict**. It has three partitions:

```
DatasetDict({
    train: Dataset({
        features: ['id', 'tokens', 'ner_tags', 'fine_ner_tags'],
        num_rows: 131767
    })
    validation: Dataset({
        features: ['id', 'tokens', 'ner_tags', 'fine_ner_tags'],
        num_rows: 18824
    })
    test: Dataset({
        features: ['id', 'tokens', 'ner_tags', 'fine_ner_tags'],
        num_rows: 37648
    })
})
```

Herein, *'ner_tags'* encodes the coarse grain tags/classes, whilst *'fine_ner_tags'* encodes the fine grain tags/classes.  There are 9 distinct coarse grain classes, and 67 distinct fine grain classes.  The `special` package reads-in the raw/original **datasets.dataset_dict.DatasetDict** and creates a new DatasetDict that focuses on a small selection of tags.  the selection of tags in focus are outlined <a href="https://d3ju6iarczw32h.cloudfront.net/src/c-eclectic-data-profiles.html" target="_blank">here</a>; the tags are stored in field named 'fine_ner_tags', and the structure of `special's` output is


```
DatasetDict({
    train: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 131767
    })
    validation: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 18824
    })
    test: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 37648
    })
})
```

The tokenization class for the T5 architecture expects a **datasets.dataset_dict.DatasetDict** of three partitions, i.e., keys: `train`, `validation`, `test`.  For example

```
DatasetDict({
    train: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 13176
    })
    validation: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 1882
    })
    test: Dataset({
        features: ['id', 'tokens', 'fine_ner_tags'],
        num_rows: 3764
    })
})
```

Each partition is a **datasets.arrow_dataset.Dataset**, and its structure has a pattern akin to

> ```
{'id': ['13487', '24698'], 'tokens': [['Salbutamol', ',', 'also', 'known', 'as', 'albuterol', 'and', 'marketed', 'as', 'Ventolin', 'among', 'other', 'brand', 'names', ',', 'is', 'a', 'medication', 'that', 'opens', 'up', 'the', 'medium', 'and', 'large', 'airways', 'in', 'the', 'lungs', '.'], ['Under', 'its', 'cultural', 'sponsorship', 'program', ',', 'Kärcher', 'has', 'supported', 'more', 'than', '90', 'projects', 'to', 'clean', 'internationally', 'prominent', 'buildings', 'such', 'as', 'the', 'National', 'Monument', 'in', 'Jakarta', '(', '2014', ')', ',', 'the', 'London', 'Eye', 'in', 'London', '(', '2013', ')', ',', 'the', 'Space', 'Needle', 'in', 'Seattle', '(', '2008', ')', ',', 'the', 'Presidents', '’', 'heads', 'at', 'the', 'Mount', 'Rushmore', 'National', 'Memorial', '(', '2005', ')', ',', 'the', 'Colossi', 'of', 'Memnon', 'in', 'Luxor', '(', '2003', ')', ',', 'the', 'Colonnades', 'on', 'St', 'Peter', '’', 's', 'Square', 'in', 'Rome', '(', '1998', ')', ',', 'the', 'Brandenburg', 'Gate', 'in', 'Berlin', '(', '1990', ')', 'the', 'Statue', 'of', 'Liberty', 'in', 'New', 'York', 'City', '(', '1985', ')', 'and', 'the', 'Statue', 'of', 'Christ', 'in', 'Rio', 'de', 'Janeiro', '(', '1980', ')', '.']], 'fine_ner_tags': [[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 6, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 2, 2, 0, 4, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 2, 2, 2, 2, 0, 0, 0, 0, 0, 1, 1, 1, 0, 4, 0, 0, 0, 0, 0, 1, 0, 2, 2, 2, 2, 2, 0, 4, 0, 0, 0, 0, 0, 1, 1, 0, 4, 0, 0, 0, 0, 1, 1, 1, 0, 4, 4, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 4, 4, 4, 0, 0, 0, 0]]}
> ```

Each list of *'tokens'* represents a sentence or paragraph; the corresponding list within *'fine_ner_tags'* encodes the corresponding tags per list.  Note, the numeric codes of *'fine_ner_tags'* map to text formats.

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
