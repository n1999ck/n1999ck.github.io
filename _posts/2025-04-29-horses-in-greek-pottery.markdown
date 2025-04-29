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

Each artifact in Bellerophon is represented as a row of a large spreadsheet, with quantitative or qualitative variables for each item stored in columns. Tabular data storage like this is very common, as it can easily be accessed programmatically. At least one photo is also provided for each artifact, an invaluable inclusion for art historical research.

I performed cleaning work on the spreadsheet to normalize variable names and row formats.

## The Graphs

My goal for this project was to create data visualizations which could show the trends in Greek pottery. 

I used Plotly.