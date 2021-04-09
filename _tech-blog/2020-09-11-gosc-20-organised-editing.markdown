---
title: GSoC 20 - Automatized support for Organised Editing Guidelines
date: 2020-09-11 12:30:00 Z
Summary Text: Here is a summary from the GSoC' 20 project that adds automatized support
  for Organised Editing Guidelines in Tasking Manager.
Feature Image: https://cdn.hotosm.org/website/gsoc-20-feature-image.jpg
Person:
- João Vitor Ramos
---

## The problem

The [OpenStreetMap (OSM)](http://openstreetmap.org/) project has established formal [Organised Editing Guidelines](https://wiki.osmfoundation.org/wiki/Organised_Editing_Guidelines), which require all groups and organized activities of mapping on OSM to report transparently on how they organize and what they are mapping on.

The [Tasking Manager](http://tasks.hotosm.org/) is the most used application in the OSM ecosystem for volunteers & professionals, to team up and coordinate mapping. Due to the large amount of organised editing done through the Tasking Manager, ensuring correct documentation is completed for all projects has become difficult. In order to ease up the user experience of fulfilling the guidelines for organized editing, the goal of my project this summer was to make the process of reporting back data for OSM automatically.

## Project solutions

To improve the documentation of organised editing for Tasking Manager projects, we thought that automatically reporting project data from Tasking Manager to the OSM could be a good solution. After that, we started with an analysis of contents and fields that are required or suggested by the organized editing guidelines, then we ran a check on whether these are already available in the Tasking Manager, or not.

Then we implemented a small proof of concept for testing out how the communication between Tasking Manager and OSM Community should occur. Although the OSM’s organized editing guidelines suggest the project wiki for reporting of organized mapping activities, we wanted to include two technical ideas for this initial test:
- Report data directly to the [OSM wiki](https://wiki.openstreetmap.org/wiki/Main_Page)
- Store files in a human-readable format in a git repository (GitHub, Gitlab, etc)

## Validating ideas

We participated in the [State of the Map 2020](https://2020.stateofthemap.org/) conference as a self-organized session in order to validate the project solutions initially thought and receive more feedback from the community.

We received some suggestions on the initial ideas, mainly for reporting data to the wiki directly instead of reporting to a git repository. After discussing internally, we reached a consensus that it would be better to use both solutions, instead of just one as thought at the beginning of the project. Coming to this architecture and also, a cool name to the project - [OEG Reporter](https://github.com/hotosm/oeg-reporter).

![](https://cdn.hotosm.org/website/gsoc-20-architecture.jpg)

* *Image 1 - Description of architecture of communication between the Tasking Manager and the OpenStreetMap*
<br><br>

---

## Implementing

After defining with the community the solutions to be used, we implemented the data report for a git repository and an instance of MediaWiki (the system used by the [OSM wiki](https://wiki.openstreetmap.org/wiki/Main_Page)) in a flask API, mainly using libraries to format data according to the format used by the [OSM wiki](https://wiki.openstreetmap.org/wiki/Main_Page) (wikitextparser) and upload and update files in a git repository (gitpython).

The most challenging part of the project's development was definitely to implement data reporting for the wiki, due to the file format used by the [OSM wiki](https://wiki.openstreetmap.org/wiki/Main_Page) having a slightly more complex syntax, but after a few weeks of study this was possible. [OEG reporter](https://github.com/hotosm/oeg-reporter) integration with Tasking Manager can be seen in the next images.<br>

### User select if the organisation is going to enable the automated OEG Report

![](https://cdn.hotosm.org/website/gsoc-20-enable-report-option.png)

* *Image 2 - Option to enable automatic project data reporting*
<br><br>

---

### Project manager saves the project normally

![](https://cdn.hotosm.org/website/gsoc-20-save-project-data.png)

* *Image 3 - Project manager saving project data*
<br><br>

---

### Project data is reported to a git repository

![](https://cdn.hotosm.org/website/gsoc-20-project-data-reported-to-git-repo.png)

* *Image 4 - Project data reported to a git repository*
<br><br>

---

### Project data is reported to a Mediawiki instance in three different pages

#### Activities list - Contains all Organised Editing activities list 

![](https://cdn.hotosm.org/website/gsoc-20-mediawiki-activities-list-page.png)

* *Image 5 - Wiki Page containing list of Organised Editing activities list*
<br><br>

---

#### Organisation page - Contain data from an organisation with a list of all its projects

![](https://cdn.hotosm.org/website/gsoc-20-mediawiki-organisation-page.png)

* *Image 6 - Wiki Page containing data from an organisation and all its projects*
<br><br>

---

#### Project page - metadata from a Tasking Manager project

![](https://cdn.hotosm.org/website/gsoc-20-mediawiki-project-page.png)

* *Image 7 - Wiki Page containing project data*
<br><br>

---

## Final Words

I would like to thank the HOT tech team for all their help and the opportunity to work with them all this summer, it was one of the best experiences of my professional and personal life to have the chance to work with so many people from different cultures and places, even more with the ultimate goal of helping people in need.