---
title: 'Export Tool Updates: New OSM Datasets for Countries on HDX and More'
date: 2020-02-16 09:00:00 Z
tags:
- HDX
- Tech
- Tools
- Export
- Code
Summary Text: 'We''ve updated the Export Tool! It''s now even easier to deliver critical
  OpenStreetMap data into the Humanitarian Data Exchange (HDX), and the hands of the
  organizations that use it, faster than ever. The update offers new export features,
  and captures how people are using it, so we can further tailor it to users'' needs.

'
Feature Image: https://cdn.hotosm.org/website/Export+Tool+Blog+1.png
Is image top aligned: true
Person: Mhairi O'Hara
Working Group:
- Technical
Project:
- HDX
---

When you're working in a disaster or emergencies, accessing the information you need as quickly and easily as possible makes all the difference. With our users in mind, we've launched the new Export Tool, which is even faster, delivering much needed OpenStreetMap data into the hands of those who need it as quickly as possible – via  [HDX](https://data.humdata.org/). It is now easier to navigate, with Export and Configuration tabs easier to find on the navigation bar.

By capturing usage metrics, we will also be able to further develop the tool with better informed and data-driven changes. We will continue to add new baseline datasets of countries to HDX, as well as add key lifeline infrastructure data for all of Indonesia to InAWARE.

## **Greater Data Outreach**

Our aim for the [Export Tool](https://export.hotosm.org/en/v3/) has always been to make it easier for users to select and download OpenStreetMap data, independent of their technical skills and experience. The Export Tool allows users to identify which map features they want to extract within a chosen area of interest. These are then converted into the file format of their choice.

It sounds simple enough, but there are still difficulties that users can encounter, such as actually knowing what features might be within the area of interest. And there is the issue of knowing what tagging names are used in OpenStreetMap for specific features. This is particularly tricky for users unfamiliar with the data structure and tagging system.

This is where the collaboration with the HDX back in 2017 was a game-changer for getting up-to-date OpenStreetMap data into the hands of even more humanitarians. HDX is an open data-sharing platform managed by the United Nations Office for the Coordination of Humanitarian Affairs, and a key online resource that individuals and organizations go to when looking for baseline map data.  There was a clear opportunity to provide OpenStreetMap building, road, waterway, and points of interest datasets to the HDX platform through the Export Tool, making accessing the data easier than ever for its users.

An integration component was built into the Export Tool so that these four OpenStreetMap datasets for specific countries could be set up to automatically export on a specified schedule. This way, any new data that is added to OpenStreetMap for the country will be extracted and hosted on HDX, ready for download and use in a variety of common GIS file formats. This integration led to the OpenStreetMap datasets being among the most downloaded on HDX in 2019, so it only made sense that we would continue to support the needs of the public with even more datasets.

This successful collaboration led to the addition of seven more datasets on top of the four outlined above. Airports and helipads, education facilities, health facilities, financial services, populated places, railways, and seaports were identified as key through discussions with our partners at [MapAction](https://mapaction.org/) to see what baseline data is generally required when they are deployed for a humanitarian response. These new datasets are now included to support the Geography & Infrastructure category of the new ‘[Data Grid](https://centre.humdata.org/introducing-the-hdx-data-grid-a-way-to-find-and-fill-data-gaps/)’ feature of HDX. This feature aims to provide data for a wide range of users and needs. The Data Grid looks at country level datasets and assesses whether the data is in a common format, tidy, geo-spatially referenced, comprehensive, and up-to-date.

![Export Tool Blog 2.png](https://cdn.hotosm.org/website/Export+Tool+Blog+2.png)

## **Baseline Preparedness Data**

The YAML code used by the Export Tool to extract features and filter specific attributes for the new seven new datasets added to the country information available on HDX is outlined below. As a quick breakdown: the ‘types’ command identifies the geometry, the ‘select’ command identifies the attributes that will be filtered, the ‘where’ command identifies the feature that is extracted from OSM. To learn more about the YAML syntax and how it is used in the Export Tool, please read the [Learn](https://export.hotosm.org/en/v3/learn/yaml) section.

**Airports and Helipads**

    types:
      - points
      - lines
      - polygons
    select:
      - name
      - aeroway
      - building
      - emergency
      - emergency:helipad
      - operator:type
      - capacity:persons
      - addr:full
      - addr:city
      - source
    where: aeroway IS NOT NULL OR building = 'aerodrome' OR emergency:helipad IS NOT NULL OR emergency = 'landing_site'

**Education Facilities**

    types:
      - points
      - polygons
    select:
      - name
      - amenity
      - building
      - operator:type
      - capacity:persons
      - addr:full
      - addr:city
      - source
    where: amenity IN ('kindergarten', 'school', 'college', 'university') OR building IN ('kindergarten', 'school', 'college', 'university')

**Health Facilities**

    types:
      - points
      - polygons
    select:
      - name
      - amenity
      - building
      - healthcare
      - healthcare:speciality
      - operator:type
      - capacity:persons
      - addr:full
      - addr:city
      - source
    where: healthcare IS NOT NULL OR amenity IN ('doctors', 'dentist', 'clinic', 'hospital', 'pharmacy')

**Financial Services**

    types:
      - points
      - polygons
    select:
      - name
      - amenity
      - operator
      - network
      - addr:full
      - addr:city
      - source
    where: amenity IN ('mobile_money_agent','bureau_de_change','bank','microfinance','atm','sacco','money_transfer','post_office')

**Populated Places**

    types:
      - points
      - polygons
    select:
      - name
      - place
      - population
      - is_in
      - source
    where: place IN ('isolated_dwelling', 'town', 'village', 'hamlet', 'city')

**Railways**

    types:
      - lines
      - polygons
    select:
      - name
      - railway
      - ele
      - operator:type
      - layer
      - addr:full
      - addr:city
      - source
    where: railway IN ('rail','station')

**Seaports**

    types:
      - points
      - lines
      - polygons
    select:
      - name
      - amenity
      - building
      - port
      - operator:type
      - addr:full
      - addr:city
      - source
    where: amenity = 'ferry_terminal' OR building = 'ferry_terminal' OR port IS NOT NULL

## **Integrations for Partner Platforms**

Continuing on from the success of the integration of the Export Tool and HDX, it made sense to build out another integration for our long time partner, the [Pacific Disaster Center](https://www.pdc.org/) (PDC). We started working with them in 2016 on the [InAWARE](https://www.hotosm.org/projects/disaster-early-warning-and-capacity-building-inaware) project in Indonesia, which focused on the data collection of key lifeline infrastructure in Surabaya and Jakarta in collaboration with the [National Disaster Management Agency](https://bnpb.go.id/) (BNPB). The city of Semarang was added in 2018, and a scale up program focused on training BNPB staff to replicate the mapping process for collecting key lifeline infrastructure data across the country began in 2019. As responsibility for maintaining and updating the data shifts to the hands of BNPB and the citizens they are collaborating with, we decided to automate how this data is brought into the disaster management platform InAWARE.

Previously static datasets were exported and provided to PDC for integration into the platform for the cities of Surabaya, Jakarta, and Semarang. Now with the new integration, similar to the setup for HDX, the exports are automatically set to update based on a specified time interval (such as hourly, daily, or weekly). This will help our partners and their end-users keep their data up to date as new information is added to OpenStreetMap. One of the key goals during the development of the integration for PDC was to set up the tool so that it will be easy to continually adapt for existing partners, as well as add new partners in future collaborations.

![Export Tool Blog 3.png](https://cdn.hotosm.org/website/Export+Tool+Blog+3.png)

## **Featured Exports and Configurations**

The HDX data model used to extract OpenStreetMap data through the tool can be found on the ‘[About](https://export.hotosm.org/en/v3/)’ page as a ‘[Featured Configuration](https://export.hotosm.org/en/v3/configurations/detail/b96a923b-8b43-437b-9dce-b4fb09530750)’. This can easily be applied to your own export by copying and pasting the YAML syntax under the ‘Feature Selection’ box into the ‘3 Data’ tab during the job creation. Currently, the OpenStreetMap data models used as part of the ‘[Global Exposure Database 4 All](https://wiki.openstreetmap.org/wiki/GED4ALL)’ and ‘[Global Healthsites Mapping Project](https://wiki.openstreetmap.org/wiki/Global_Healthsites_Mapping_Project)’ are also featured configurations. Please let us know if you have any other data models that you would like to feature on the Export Tool. Get in touch via the #export-tool channel on the [HOT Slack](https://slack.hotosm.org/).

Similarly, there are ‘Featured Export’ jobs listed on the ‘[About](https://export.hotosm.org/en/v3/)’ page, which are generally focused on OSM extracts created in response to a HOT activation and cover the exact area of mapping interest outlined in the Tasking Manager. These exports are also set to update automatically based on the selected frequency (such as hourly, daily, or weekly), so that disaster response partners can keep their data up to date as new data gets added to OpenStreetMap by mappers.

![Export Tool Blog 4-736828.png](https://cdn.hotosm.org/website/Export+Tool+Blog+4-736828.png)

![Export Tool Blog 5.png](https://cdn.hotosm.org/website/Export+Tool+Blog+5.png)

## Aggregated Tool Stats

A major focus in enhancing the Export Tool admin functionality is to capture additional user statistics to better understand how, where, what, and when the service is being used. This will help pave the way for future rounds of development. The stats that are currently being collected and aggregated are the number of new users of the tool as well as the number of exports being generated and their geospatial distribution across regions. These stats can be filtered and disaggregated based on the past week, past month, past three months, past six months, past year, past two years, as well as custom time intervals.

![Export Tool Blog 6.png](https://cdn.hotosm.org/website/Export+Tool+Blog+6.png)

![Export Tool Blog 7B-74b54c.png](https://cdn.hotosm.org/website/Export+Tool+Blog+7B-74b54c.png)

These stats are visually supported with a map of the exports on the right side of the page, as well as the ability to export the information in a CSV file for further analysis and data visualization by users. Please note that the stats page is currently only accessible to admin users of the tool, but there are plans to open this to the general public in the next round of development.