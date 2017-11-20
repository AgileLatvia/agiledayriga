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
  url: "http://www.agiledayriga.lv/events/2016/index.html"
```
This change will affect both menu and `sitemap.xml`.

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

1. Copy one of the existing 'About' snippets to the new one which will be used this year: `cp _includes/2016-about.html _includes/2017-about.html`
2. Edit `_includes/2017-about.html` the way you need.
3. Edit `_includes/all-about.html` and add the new snippet there.
4. Enable new block.
You should see the block on the page and the new menu item.

## Step 3
Then we should add and enable 'Social' snippet. It contains two Twitter streams one filtered by our community account and another by the conference hashtag. You should go to Twitter and create a widget there first.

1. Copy one of the existing 'Social' snippets to the new one which will be used this year: `cp _includes/2016-social.html _includes/2017-social.html`
2. Edit `_includes/2017-social.html` the way you need.
3. Edit `_includes/all-social.html` and add the reference to the new snippet there.
4. Enable new block.

## Step 4
Now it's time to add CFP snippet. As this website is static, you should prepare some form to embed or link. In our case we're going to use Google Forms, but it's possible to use any other web service. For example, Woofoo.

1. Copy one of the existing 'CFP' snippets to the new one which will be used this year: `cp _includes/2016-cfp.html _includes/2017-cfp.html`
2. Edit `_includes/2017-cfp.html` the way you need.
3. Edit `_includes/all-cfp.html` and add the reference to the new snippet there.
4. Enable new block.

## Step 5
If we know the venue then we can put it on our site. In order to do that follow the steps:

1. Use the existing venue or copy a file of existing one into a new file in order to create a new venue. Example: `_includes/islande-hotel.html`
2. When we are done with the snippet we should update `_includes/all-venue.html` and map the snippet to appropriate year. Check how it was done for previous conferences.
3. Final step is to open `index.html` and set `venue-block` variable to `on`.

## Step 6
Time for the sponsors, if there're some of them at the moment. 

1. Open `index.html` and set `sponsors-block` variable to `on`. By doind this you will enable this block on the conference page as well as menu item for this section.
2. Then open `_data/sponsors.yml`
3. Create a section for the conference year you need and start to add data.
4. It should be taken into consideration that we have several levels of sponsorship: platinum, gold, silver, info. There're differences between how the sponsors will be displayed based on level of the sponsorship: platinum sponsors have the biggest size of the logo and the additional text; silver and info have smallest size of logos; gold is somewhere in between.
5. Sponsors logos should be stored in `img/sponsors/`. Adding logos do not forget to make them of equal height and center the logo both vertically and horizontally.
6. There are two more options to alter how this block will be rendered:
  * `show-subtitles` will display the sponsors section sub titles, if they are provided.
  * `show-captions` will display the promo text provided by sponsor. It's a default way of rendering for platinum sponsors, but it can be enabled for gold and silver sponsors by setting this parameter to `on`. `show-captions` are always `on` for platinum sponsors and always `off` for info sponsors.

Here's an example:
```
2017:
  show-subtitles: "true"
  platinum:
    title: "Platinum Sponsors"
    sponsor01:
      title: "Evolution Gaming"
      image: "/img/sponsors/evolution-gaming.png"
      url: "https://www.evolutiongaming.com/"
      promo: "Some promo text here."
  gold:
    show-captions: "true"
    sponsor01:
      title: "Twino"
      image: "/img/sponsors/twino.png"
      url: "https://join.twino.eu/en/"
      promo: "Another promo text here."
  silver:
    sponsor01:
      title: "Scrum Alliance"
      image: "/img/sponsors/scrum-alliance.png" 
      url: "http://www.scrumalliance.org/"
```

## Step 7
It's about time to close CFP. Well, it makes sense to announce a couple of speakers at the same time.

1. Open `index.html` and set `cfp-block` variable to `off` and `sessions-block` to `on`.
2. Then open `_data/sessions.yml`
3. Create a section for the conference year you need and start to add data.
4. Please note, that if some data is not available do not set anything. `""` is treated as `empty` value.
5. Please note, that speaker's photo should be stored in `img/speakers/`. It's also important to preserve the balance between size and quality.
6. If there're more than one speaker feel free to add a block for the second one. Check the example below.
7. Also take into consideration that `session01` is used for case sensitive sorting. For example `session12` will be shown below `session05`.
8. Please notice that you can define the day. This field must have a value. If only one day is defined, then it won't be shown.

Here's an example:
```
  session01:
    day: 1
    time: "10:00 - 11:00"
    place: "Room A"
    title: "Nexus: How We Do Scrum with 150+ People"
    about: "Nexus is a framework for scaled Scrum developed by Scrum co-creator Ken Schwaber and Scrum.org community. It addresses the most painful problems of scaled development – dealing with dependencies and building 'Done' integrated software every iteration. In our short talk, we are going to explain the key concepts of Nexus and illustrate them with our own case study where 150+ people successfully do Scrum to build software for a big North American retail company using Nexus."
    slides: 
    video: 
    speakers:
      speaker01:
        name: "Artem Kolyshkin"
        bio: "Artem Kolyshkin is a Senior Delivery Manager at EPAM with wide experience of product and project delivery. Currently implementing the Nexus framework on a project with 150 + people."
        photo: "/img/speakers/artem-kolyshkin.jpg"
        blog: 
        facebook: 
        twitter: 
        linkedin: "https://www.linkedin.com/in/akolyshkin/"
        google-plus: 
      speaker02:
        name: "Konstantin Razumovsky"
        bio: "Konstantin Razumovsky is an Agile Coach and Professional Scrum Trainer by Scrum.org. He has an extensive hands-on experience as a Java Developer, Scrum Master, and Project Manager."
        photo: "/img/speakers/konstantin-razumovsky.jpg"
        blog: "http://proscrum.by/"
        facebook: 
        twitter: 
        linkedin: "https://www.linkedin.com/in/razumovsky/"
        google-plus: 
```

## Step 8
How to Add Tickets? 

1. Copy one of the existing 'Tickets' snippets to the new one which will be used this year: `cp _includes/2016-tickets.html _includes/2017-tickets.html`
2. Edit `_includes/2017-tickets.html` the way you need using the pre-generated widget from Eventbrite: open 'Manage Event', then click 'Widgets' from 'Invite & Promote' section, then select 'Ticket Form'
3. Edit `_includes/all-tickets.html` and add the reference to the new snippet there.
4. Enable new block by opening `index.html` and setting `tickets-block` variable to `on`.

Here's an example of `_includes/2017-tickets.html`:
```
  <!-- tickets -->
  <div id="tickets" class="page color-1">
    <div class="inner-page">
      <h2 class="page-headline">Tickets</h2>
    </div>
    <div class="row inner-page">
      <div class="col-md-12">
        <div style="width:100%; text-align:left;"><iframe src="//eventbrite.com/tickets-external?eid=32462037829&ref=etckt" frameborder="0" height="400" width="100%" vspace="0" hspace="0" marginheight="5" marginwidth="5" scrolling="auto" allowtransparency="true"></iframe><div style="font-family:Helvetica, Arial; font-size:12px; padding:10px 0 5px; margin:2px; width:100%; text-align:left;" ><a class="powered-by-eb" style="color: #ADB0B6; text-decoration: none;" target="_blank" href="http://www.eventbrite.com/">Powered by Eventbrite</a></div></div>
      </div>
    </div>
  </div> <!-- /tickets -->
```

## Step 9
How to Setup Conference Schedule? 

1. Assuming that you have already created an event in Lanyrd service set `schedule-lanyrd` variable in `index.html` file. Use the link to schedule from event created there.
2. Set variable `schedule-status` to `on`.

```
  schedule-status: "off"
  schedule-lanyrd: "http://lanyrd.com/2017/adr17/schedule/?day=jul-07&fullscreen=1&view=grid"
```

## Step 10
How to Switch Off Tickets and Event Microdata?

1. Disable tickets by opening `index.html` and setting `tickets-block` variable to `off`.
2. Disable microdata by opening `index.html` and setting `event-microdata` variable to  `off`.

## Step 11
How to Switch Off Schedule?

1. Set variable `schedule-status`  in `index.html` file to `off`.

## Step 12
How to Add Slides and Videos?

1. Open `sessions.yml` and add links to `slides` and `video` variables in appropriate session.
2. You may add links one by one whenever you want.

-----

### To Be Developed
1. Add HTML minification. :x: 
2. Add HTTPS if possible. :heavy_minus_sign: (not available for custom domains)
3. Add Events microdata. :white_check_mark: 
4. Fix the issue with speakers if there're no SMs defined. In this case the 2nd speaker's block is aligned improperly. :white_check_mark: 
5. Update event schema.org markup with Eventbrite link and data. :white_check_mark: 
6. Use the same approach from Info sponors for grid view of other types of sponsors, except Platinums. :white_check_mark: 

### To Be Done
1. Move 2015 under standard flow. :white_check_mark: 
2. Move 2014 under standard flow. :white_check_mark:
3. Move older conferences under standard flow. :white_check_mark: 
4. Support more than 1 day for sessions. :white_check_mark: