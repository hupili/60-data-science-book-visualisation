# 60-data-science-book-visualisation

![Visualisation of 60 data science book](https://raw.githubusercontent.com/hupili/60-data-science-book-visualisation/master/assets/data-science-books-graph.png)

A live version can be found on [kumu.io](https://kumu.io/hupili/60-free-data-science-book#60-free-data-science-book)

## Background

[Initium Lab hods a Jackathon](http://initiumlab.com/blog/20150922-jackathon3-review/):
Read a data science book in 8 hours.
We want to analyse those books. 

## Get the Raw Data

Combine `http` and `pquery` for a quick command-line hack.

```
%http --body 'http://www.kdnuggets.com/2015/09/free-data-science-books.html' | pquery '.three_ul li strong a' -f '"{text}",{href}' > books.csv
%http --body 'http://www.kdnuggets.com/2015/09/free-data-science-books.html' | pquery '.three_ul li em' -p text > authors.csv
%http --body 'http://www.kdnuggets.com/2015/09/free-data-science-books.html' | pquery '.three_ul li' -p html | grep '</em>' | sed 's/<\/em>/    /g' | cut -f2 | sed 's/[^0-9]//g' | tr -d ',' > years.csv
```

Result:

```
%wc -l *.csv
62 authors.csv
61 books.csv
62 years.csv
185 total
```



