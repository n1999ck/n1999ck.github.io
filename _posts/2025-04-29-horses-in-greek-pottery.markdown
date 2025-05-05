---
layout: post
title:  "Horses in Ancient Greek Pottery: Exploring The Data (WIP)"
date:   2025-04-29 10:50:52 -0400
categories: art history greek
---

# Introduction

It is difficult to overstate the importance horses held in the ancient Greek world. 
Not unlike our own society, equestrianism was generally restricted to the upper classes. A good horse could cost about as much as a skilled worker earned in a year and a half. {cite from symposium video and/or book}. Those who could afford horses could join the *hippeus,* or cavalry, the second-highest social class in Athens. Members of the *hippeus* served alongside hoplite footsoldiers in combat. Individual horses could also gain social reverence. Bucephalus ("ox-headed"), Alexander the Great's warhorse, was said to have cost 13 talents, roughly equivalent to about $325,000 in today's money. [https://en.wikipedia.org/wiki/Bucephalus#cite_note-5] Bucephalus became so famous as part of Alexander's story that he became almost a mythical, legendary figure. Coins from the time rarely depicted rulers before Alexander, but Bucephalus surpassed kings by numismatic representation. {symposium, probably book}.

Archaeology deals heavily with pottery. Fired clay gains outstanding durability, allowing for excellent preservation as opposed to organic materials like wood and leather. In their time, clay vessels served practical, decorative, and ritual purposes, and were often painted with mythical, historic, or everyday scenes. Potters often portrayed horses on their vessels, creating a record of how the Greeks understood horses' roles in society.

## The Dataset

This project depends heavily on (Bellerophon)[https://pandoradata.earth/en/dataset/bellerophon], a dataset of black-figure pottery from the Geometric, Orientalizing, and Attic periods depicting horses and other equines. The dataset was prepared by Czech researcher Romilda Tengeriová as part of her master's thesis. Tengeriová has continued to research ancient Greek horsemanship. Bellerophon was released for public use under the Creative Commons Attribution Share-Alike license, contributing to a growing movement to publish data openly over the Internet for research and analysis.

Each artifact in Bellerophon is represented as a row of a large spreadsheet, with quantitative or qualitative variables for each item stored in columns. Technically, it's really just a large text file with every value separated by commas (a CSV file). Tabular data storage like this is very common, as it can easily be accessed programmatically. At least one photo is also provided for each artifact, an invaluable inclusion for art historical research. 

I did some manual standardization on the spreadsheet to normalize variable names and row formats. Some entries had little errors like extra spaces, which needed fixing as computers interpret "C" and "C " as different values

To prepare for graphing the dataset, I wrote some scripts to get lists of every column name as published, unique entries in each column, and the number of unique entries per column. This information was helpful for getting a sense of the data.

## The Graphs

My goal for this project was to create data visualizations which could show the trends in Greek pottery. 

I used Plotly, a high-level Python library for graphing data. Plotly is surprisingly straightforward to work with. To create a pie graph, for example, all I needed to do was call the pie graph function and pass it the dataset, the name of the column to graph, and visual details like the graph title or labels. With that information, Plotly calculates the size of each graph segment, creates the graph, and deploys it as an interactive local web page. 

The difficult part was determining which parts of the data to visualize. I started with some simple, obvious graphs, like pie charts of vessel types and local styles. 

I made three pie charts. One shows the types of vessels in the dataset, another shows the local styles of the vessels, and the last shows the amount of complete vessels recorded. These have simple messages, but can still be of interest. The first shows how popular amphorae were, with their slice of the chart nearly four times the size of kraters in second place. The chart of local styles shows that the majority of the vessels were Athenian or Attic, with less than a third from other areas. The chart of complete vessels shows that nearly 80% of the artifacts were found complete, far more than I expected.

Chronological information was of interest to me, so I made a histogram of the medians of each item's given date range. Python supplies a library for working with dates and time, but it doesn't support BCE dates, so I treated the years as simple negative integers. The dataset also provided a relative date for each vessel, but these were unordered and a little inconsistent, so I didn't visualize them. I started by making a histogram, which was essentially a bar chart of the number of vessels per year. The histogram showed an early spike in vessels from around 725 BCE, another around 675 BCE, and a more gradual increase to the overall peak between 600 and 500 BCE. I'm hesitant to take the graph's increases and decreases at face value, since medians may not accurately reflect the data. However, the graph speaks to the general trend - horses appeared on Greek pottery for hundreds of years.

I also made a box plot of median years. It does a better job of showing the overall skew of data between outliers. It also illustrates why I don't put much stock into the histogram, as the lines of items on some years shows that many had very similar ranges that can't reflect growth trends in detail. However, it's harder to read the box plot for the general areas of high frequency.

The dataset provided latitude and longitude information for some of the finds, which gave me a chance to try out GIS in a very basic way. To show which areas had supplied the most vessels, I made a bubble map. Each bubble's size represents the number of finds at a given point on the map. I used a GeoJSON polygon to focus the map on the correct area. The polygon is just a list of coordinates making a rectangle around the finds. Mapping the finds shows the finds scattered through modern Italy and Greece, with most of the items from near Athens and Rome. Some outliers are in Egypt and modern Ukraine. The map shows an interesting distribution of sites, though I wonder if the highly concentrated areas reflect areas of current interest and funding more than anything.

I also wrote some rudimentary ways to view the vessels, either randomly or by an attribute like the most horses recorded. These functions find the vessel's ID, which can be used to get its image folder. The image is opened with Scikit-image, which allows Plotly to display it like a graph. So far, I've written viewers that pull up the vessel with the most horses, pegasi, or hippalektryon, and one that randomly selects a vessel to display. I'm glad I did this as visuals are so obviously crucial for art history, but it's clear that a more user-friendly viewing interface is needed.


## Deliverables

I started with only a vague idea of how to present/deliver my work, an oversight which caused some problems later. My vague plan was to combine everything into a website. However, I later found that Plotly alone isn't meant for creating pages with multiple graphs at once. They offer Plotly Dash for creating "dashboards" of graphs, but using Dash would require me to create the entire webpage in Python and heavily restructure my code. Web development is usually done in JavaScript, and I wanted the control I get by writing my own page as opposed to having Dash do it for me by converting Python to JavaScript. 

So, I started writing a Jupyter notebook instead. Jupyter notebooks are essentially text documents with embedded code snippets. This option went well at first, but I soon found that the notebook couldn't deploy Plotly graphs or reliably install dependencies. I liked the notebook's freedom to explain my code, but it's more important to get the code functioning.

In the end, I ran out of time to use another option and am turning in the graphs as image files. I plan to continue by converting my existing work to use Plotly's JavaScript library, then create a webpage or pages with my usual web development tools to publish the graphs in their interactive form as well as a better way to view the images of the vessels.

## Future Plans

This project has opened my eyes to a world of possible next steps. First, I'll need to find more ways to visualize the data for deeper insights. My graphs have all shown just one variable at a time (year, completion, location, etc.), limiting their possible insights. Multivariate graphs could be much more informative, but to make them I need to find out what information to compare and how. This is much more straightforward for quantitative data than the qualitative data that makes up much of Bellerophon. Regardless, I believe it will be worth figuring out. As Edward R. Tufte notes in his seminal *The Visual Display of Quantitative Information*, "graphical excellence is nearly always multivariate."

I'd also like to find a way to show images on my existing graphs, especially for outliers and other points of interest. 

This dataset could also be combined with others for new insight. The site hosting Bellerophon also has a dataset of horse remains around the Mediterranean, which could be interesting mapped alongside the pottery finds.

In general, I hope to do more data analysis on art history topics. Art history isn't the most data-forward field, but there are datasets available that are worth examining. Some major museums have great open data programs that I've looked at briefly before and would love to revisit now. The Metropolitan Museum publishes data on hundreds of thousands of items, and the Smithsonian has millions in its online datasets. The Smithsonian also publishes 3D scans of everything from orangutan skulls to Greenough's buff George Washington statue. The possibilities for future exploration are endless and exciting.
