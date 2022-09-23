### Table of Contents
In the beginning we brainstormed on creative ways to classify the Websites. Although we were not able to integrate everything, we wanted to submit them as supplementary content. Here, you can read about initial ideas of our project. These could be added in the future to improve the metrics of the models: 
- [In- and out-links](#links)
- [Wikipedia Abstract](#abstract)
- [cylex.de, unternehmensregister.de](#cylex)

  
---

<a name="links"></a>
#### In- and out-links
As in- and out-links are used in web analysis, we explored the idea of using them as a feature to classify websites. However, after reasearching it, we decided not to implement it. As the paper ["Content-based and link-based methods for categorical webpage classiﬁcation"](https://github.com/pds2122/capstone-project-kabobe/blob/main/supplementary_file/Content-based%20and%20link-based%20methods%20for%20categorical%20webpage%20classiﬁcation.pdf) shows, the links add a lot of noise to the dataset and are no beneficial data point.

<a name="abstract"></a>
#### Wikipedia Abstract
Also an idea was to filter the name from the url, which is possible with de Bibliotek `urllib.parse`. Using a webscraper, the name could be searched on Wikipedia and the abstract can be taken. This would be another column of information that could be useful to predict the industry label.

<a name="cylex"></a>
#### cylex.de, unternehmensregister.de
Similar to the suggestion above, you could use `urllib.parse` to take the name of the company from the url and paste it to pages like cylex.de or unternehmensregister.de using a scraper to get more information. Possibly an API can also be integrated here (if available).
