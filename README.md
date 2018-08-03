# Primer_Quicksilver

Quicksilver is an artificial researcher that reads documents and writes out information about entities. Our
system ingests both news and scholarly articles as they are published each day, extracts notable people, places
and concepts from those documents, and writes a summary of the most novel and important information it has
learned.


This dataset is a representation of the data we have and how entities from various sources have been disambiguated and linked by the system.


The dataset can be downloaded [here](https://s3.amazonaws.com/primer-quicksilver-dataset/quicksilver_v0/qs_data.zip). (138.2MB compressed, 406MB uncompressed) 

### Collaborators :
* Allen Institute for Artificial Intelligence (AI2)

### Data Sources :

* Primer news corpus (500m news docs from English-language sources published since 2015)
* Semantic Scholar Open Research Corpus (date of our download: 2017-06-01)
* Wikipedia dump - 2018-01-20
* Wikidata dump - 2018-02-05


### Criteria for inclusion of people:
* author of a paper in AI2 research corpus or have a wikipedia/wikidata page
* has at least 10 papers in the Semantic Scholar Open Research Corpus (S2)
* has one published paper in S2 since 2015
* has at least 100 total citations their S2 papers

or

* has a wikipedia article and/or wikidata entry

### Data stats:

* \# people - 36268
* \# people with English Wikipedia articles - 4843
* \# news docs - 329,422
* \# news mentions - 1,113,447


## Attributes
Schema:
```
name  string
name of the scientist
…
s2_affiliations list
scientist affiliations from semantic scholar dataset
…
s2_paper_ids list
semantic scholar paper ids attributed to the scientist
…
s2_id string
id of the scientist in semantic scholar dataset
…
en_wikiUrn list
wikipedia urn for the scientist
…
P21 list
gender fetched from wikidata if present or calculated using census data and news mentions
…
primer_id string
primer generated unique id_
…
wikidata_id string
id_ of the person in Wikidata
…
news_docs list
disambiguated news docs mentioning the scientist
    url string
    url of the news article
    …
    publication_date string
    date  the article was published
    …
    title string
    title of the news article
    …
    mentions list
    sentences where the scientist is mentioned
        text string
        sentence mentioning the scientist
        …
        is_quote bool
        sentence is a quote or not

```
### Example


Schema:
```
{
  "s2_affiliations": [],
  "en_wikiUrn": "Paritosh_Pandya",
  "name": "Paritosh Pandya",
  "news_docs": [
    {
      "url": "http://www.mid-day.com/articles/21-things-to-do-around-mumbai-from-june-13-to-june18/17327195",
      "publication_date": "2016-06-12",
      "mentions": [
        {
          "text": "Professor Paritosh Pandya, a computer scientist and an ardent music lover, will throw light on these questions.",
          "is_quote": false
        }
      ],
      "title": "21 things to do around Mumbai from June 13 to June 18"
    }
  ],
  "s2_paper_ids": [],
  "P21": [
    "Q6581097"
  ],
  "primer_id": "Pr31261",
  "wikidata_id": "Q15713163"
}

```

## Versioning

This is v.0 of the dataset. Future releases will include additional scientists and additional structural data for the purpose of enriching and improving Wikidata, Wikipedia, and other public data resources.

## Authors

* **Primer Technologies Inc.** 

## License

See the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Many thanks for advice and feedback from Dario Taraborelli, director of research, Wikimedia
* Oren Etzioni and the Semantic Scholar team at the Allen Institute for AI, Seattle

