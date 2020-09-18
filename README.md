# Assessing PagSeguro's complaints at ReclameAqui and comparing with its stock perfomance :rage: :chart_with_upwards_trend: :rage: :chart_with_downwards_trend:

:file_folder: Kaggle's Global Shark Attack (https://www.kaggle.com/teajay/global-shark-attacks/)

Repository includes: 
* Yahoo Finance's API integration
* Reclame Aqui's web scraper
* Juyter notebooks for parsing RA's data and finally transformed it to a wordcloud

### How PagSeguro's stock performed over the last year? Does the number of recent complaints correlate with stock performance? :money_with_wings:

As most stocks, PagSeguro **plunged** amid Covid-19 uncertanties. It then **quickly picked up**, reaching the same price as last year in August.
Interestly, number of complaints increased ~30% over the 6-mo period - coincidentally with the lockdown in Brazil.

However, **there is no enough evidence to correlate PagSeguro's share price to the recent increase in complaints at ReclameAqui** 


### Given that last data on complaints, what are PagSeguro's main pain points according to its clients? :broken_heart:

* Image below illustrates main common terms in the complaint dataset, after normalizing for common stop words and non-insightful vocabulary:

<img src="imgs/wordcloud.PNG">

As we can surmise from the wordcloud:
>* Most common expression "entrei em contato" suggest that clients turn to ReclameAqui after exhausting options to resolve with PagSeguro

>* Expressions "conta pagseguro" (current account) and "cartao de credito" (credit card) suggest that those products might **detract customers' satisfaction**

>* PagSeguro flagship product, moderninha (a yellow credit card machine) is not a common term, which might that it **promotes customers' satisfaction**

## Anyhow, how was the gathering process? :microscope:

### Phase 1 (aka piece of :cake:): Integration with Yahoo Finance's API:

* Unfortunately, Yahoo deprecated their Finance API in 2017. Fortunately for us, Python has a stable API called yfinance, which does pretty much the same thing
* Adjusted share prices of PagSeguro and its peers were then scrapped by using the yf.download method 

### Phase 2 (aka :rocket: science): Scrapping ReclameAqui's website:

* Unfortunately, RA's website can only be scrapped using selenium, which slows down the overall process
* Scraping process was divided into two consequent streams:
>* Stream 1: Selenium gathered all the complaint links of PagSeguro available at RA: ~50k links were then consolidated into .txt files (RA allows selenium to scrape 10 links per interaction)  

>* Stream 2: Selenium then opened each complaint link to gather useful data for later parsing - more especifically: complaint title, body, status, date, city/state of the client

