# Agile Day Riga

This is 'Agile Day Riga' conference website.

You can fork this repository if you want and use it and the flow described below. Just take into consideration that we're using the proprietary theme ['The Story'](https://wrapbootstrap.com/theme/the-story-flat-business-template-WB05N1SL7).


# Setting up the New Event
## Step 0
In order to setup the conference site for the new conference we need to move the latest one to the archive:
- Create the new folder under `events`. In out case `2016`.
- Copy `index.html` to `events/2016`.
- Copy `_layouts/default.html` to `_layouts/layout-2016.html`.
- We have sessions and sponsors data stored in `_data/sessions.yml` and `_data/sponsors.yml` for every conference. At this point of imlementation nothing needs to be done. Old conference page will use a proper data wherever they are located on the website.
- Add year and a link to the archived conference as a new row at the top of the list in `_data/events.yml`. Like this:
```
2016:
  title: "2016"
  url: "/events/2016/index.html"
```

- If done right when you browse http://127.0.0.1:4000/events/2016/index.html you should see the copy of recent conference.

## Step 1
Let's start with preparing our website for the new conference.

First we will need to setup a new theme. That's easy. Just copy one of the 'The Story' templates into `<year>.css`.
```
cp css/the-story-purple.css css/2017.css
```
Then we need to update the `index.html` which is stored in the root folder of our website.

Most of the configuration can be done step by step. You should change variables in `index.html` and create event specific files in `_includes` folder. But for now ensure that all blocks are set off.
```
layout: default
title: "Agile Day Riga 2017"
year: 2017

motto: "Join, Explore, Learn!"
date: July 7-8, 2017
venue: Radisson Blu Daugava
twitter-hashtag: adriga17

about-block: "off"
cfp-block: "off"
sponsors-block: "off"
sessions-block: "off"
tickets-block: "off"
feedback-block: "off"
venue-block: "off"
social-block: "off"

call-for-sponsors: "on"
call-for-sponsors-proposal: "https://docs.google.com/presentation/d/1mWhCVGqh2k5jWMAwlMFiYaCHO9nZVo_YSNAajrfT63g/edit?usp=sharing"

schedule-status: "on"
schedule-lanyrd: "http://lanyrd.com/2017/adr17/schedule/?day=may-25&view=grid"
```
By setting variables 'on' or 'off' you will make them and menu item related to them visible on the website. However, please, note that if block is missing it won't be displayed. See below for details.

## Step 2
Let's start with 'About' block:
1. Copy one of the existing 'About' snippets to the new one which will be used this year:
```
cp _includes/2016-about.html _includes/2017-about.html
```
2. Edit `_includes/2017-about.html` the way you need.
3. Edit `_includes/all-about.html` and add the new snippet there.
4. Enable new block.
You should see the block on the page and the new menu item.

## Step 3
Then we should add and enable 'Social' snippet. It contains two Twitter streams one filtered by our community account and another by the conference hashtag. You should go to Twitter and create a widget there first.
1. Copy one of the existing 'Social' snippets to the new one which will be used this year:
```
cp _includes/2016-social.html _includes/2017-social.html
```
2. Edit `_includes/2017-social.html` the way you need.
3. Edit `_includes/all-social.html` and add the reference to the new snippet there.
4. Enable new block.

## Step 4
Now it's time to add CFP snippet...

## Step 5
If we know the venue then...




### To Be Developed
1. Add HTML minification.
2. Add HTTPS if possible.
3. Add Events microdata.

### To Be Done
1. Move 2015 under standard flow.
2. Move 2014 under standard flow.
3. Move older conferences under standard flow.