---
layout: post
title: Let's Hike! Malaysia
description: A project to pinpoint the targeted peaks of hiking expeditions on an online map.
keywords: normalize.css, mini css framework, rapid development
---

![Screenshot](http://i.imgur.com/agOTLeg.png)

## About the project

**Let's Hike! Malaysia** is the name of this project. This project is about a map site that uses Google Map API and JSON data to pinpoint a collection of targeted peaks of hiking expeditions such as mountains, hills and waterfalls around Malaysia.

Each marker on the map site contains the information of the **peak name**, **GPS coordinates**, **elevation profile** (in meter) and **remark** or **short description** about it. The color of the marker is based on the elevation categories;-

* `blue`: 0 - 199m
* `green`: 200m - 499m
* `yellow`: 500m - 999m
* `red`: 1000m - 1999m
* `purple`: 2000m and above

## Project website

The map site currently can be viewed here: [heiswayi.github.io/lets-hike](http://heiswayi.github.io/lets-hike/). Later, if I have enough (a lot) of the data, I might purchase a specific web domain for the site.

## Data

The data is in the JSON file (**data.json**) which can be viewed [here](https://github.com/heiswayi/lets-hike/blob/master/data.json) in [the GitHub repository](https://github.com/heiswayi/lets-hike).

## Contributions

Anyone who is interested / willing to help to contribute the data, feel free to do so by telling me on my [Twitter](http://twitter.com/HeiswayiNrird) or [Facebook](https://www.facebook.com/profile.php?id=1257583160), or if you are familiar / having GitHub account, can submit it by [creating an issue](https://github.com/heiswayi/lets-hike/issues/new) or [forking the project](https://github.com/heiswayi/lets-hike/fork) then [create the pull requests](https://github.com/heiswayi/lets-hike/pulls).

## Accuracy of the data

Please note that, the data provided on the map site may not accurate as 100% because different people might record at different point of peak on different type of GPS devices. These will result a slightly difference in GPS coordinates and elevation profiles. However, I'll try to use the best one. So, any contribution to the data is really-really welcomed here.
