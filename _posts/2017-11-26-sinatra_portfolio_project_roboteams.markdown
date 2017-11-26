---
layout: post
title:      "Sinatra Portfolio Project: RoboTeams"
date:       2017-11-26 18:08:20 -0500
permalink:  sinatra_portfolio_project_roboteams
---

My origianl plan for this app was to build a team registration app so teams could sign up to attend a local robotics event or competition, with a few modifications this app could still be used for that purpose, however it is currently structured to store information about teams that a particular user is keeping track of, I for one have 3 robotics teams I coach and many other teams I mentor and like to follow.

I have seen some wonderful digital tools to help with planning relational databases and mapping out file structures, however I found myself resorting back to pen and paper as I planned and worked through this project. I am a very visual person and seeing things digitally works great, however I found myself longing for a more concrete workspace to refer back to without having to switch tabs or windows, so out came the notebook. 

I started by writing down what I wanted my app to be able to do from the index page, what links or buttons the user should be able to click on from there and where that would lead. Then once they were loggind in, where would they go? What should they see when they log in, what buttons or links will they need to have on that page to create, see and manipulate their list of teams? From here I started drawing out my tables and listing the attributes each object would have and how they would relate. This helped me list out the models, views and controllers I would need to create.  I decided to have the CRUD part of the app be based around the teams, so that the user would have full create, read, update and delete functionality with their teams, but not neccessarily for the team members or sponsors. 

Team members will only belong to one team, but at the same time a team will have many members. As the owner of the team you are able to uncheck or remove members from the team, edit a team member's name and title or add new members to your team, but you cannot delete a member once it has been created.  FIRST robotics teams like to keep track of their alumni. ;)

Team sponsors often sponsor more than one team(creating a has_many/has_many relationship), so I wanted every user to be able to see all of the sponsors, but I did not want users to be able to delete sponsors since that would mess with other teams sponsor lists.  Thus when creating a team you have checkboxes for each of the existing sponsors and a box to create a new one if you have one that is not on the list.  I also added a sponsor list page so that you can see all of the current sponsors, (edit their name if there is a mistake) and create new ones to assign to your teams there.

While building this app I was surprised at how many files and folders I ended up creating for what seemed like pretty simple relationships between my objects.  I found that I tend to get involved in writing code and forget that I am suppsed to be committing my changes regularly, so I may be setting a timer to make sure I commit my changes on a more regular basis, not just when I am finished working for the day. I also need to go back and review over css stylsheets.  I ended up just including some inline styles in my layout.erb, but I know this is not the best way, it has just been a while since I worked with css stylesheets and I need to go back and refresh my memory.  In addition I need to work more with the flash messages and getting them to look the way I want them.


[https://github.com/eland05/robo_teams_sinatra](https://github.com/eland05/robo_teams_sinatra)
