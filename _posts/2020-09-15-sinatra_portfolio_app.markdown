---
layout: post
title:      "Sinatra Portfolio App:"
date:       2020-09-15 18:37:51 +0000
permalink:  sinatra_portfolio_app
---

### Creating a web app to track Symphony personnel and their service counts.

During the pandemic, a serious problem for the Houston Symphony as musicians return to the stage is the balance of work. Each program that the symphony does will have a certain number of rehearsals and concerts associated with it. These are called "services", and it is the simplest way to track how much work a musician has done over the season.

Managing each section involves attempting to keep these service counts similar. Making sure one musician does not play every program while others barely get any stage time is crucial to keeping morale high and avoiding injuries from overuse. 

With that in mind, I set out to create a simple database and system of views to allow an average user to navigate each section and compare service counts.

Each musician belong to a section, allowing sections to have many musicians. Each musician will have many programs that they have performed, and each program will in turn have many musicians. This required a join table, which was simple enough to set up. 

I created views to allow a user to see all sections, all musicians, and all programs. These will likely be the most used pages of the app for an average viewer who wants a general sense of the breakdown of services across any section, or to just see general info about each program. To allow for quick navigation, I assigned the name of each section and musician to its id page to allow a user to get more detailed information.

Since we don't necessarily trust our musician colleagues with the responsibility of adding to, editing, or deleting from our database, we hid these features from a user who is logged in with a user_id. I decided to create a separate class of login for an admin, and reveal the new, edit, and delete buttons only when an admin_id was detected in the session hash. The admin signup process occurs when someone enters an admin key into the appropriate field in the signup form, and their account exists as the separate class Admin. 

The security of this process is certainly not very robust, and I would never trust the sensitive data of payment info or personal info with this level of key check. However, for a simple logistical app for orchestra management to use, I think this would be apropriate. When setting up the app for an institution, a unique key could be defined within the Admin class to give more protection to the admin capabilities.

I enjoyed doing some rudimentary css selecting and modification to get the index views of sections, musicians, and programs to be a little easier to parse visually. I could definitely see this kind of program being an asset to a personnel manager who wants a simple interface for visualizing how each section is balanced as far as service count.

If I were to polish this project up for some kind of release, I would do some more beautification to the styles to make the information even more digestable and adaptive to mobile use, and add the ability to record a subset of the services of each program for a musician. Not every musician plays every service of a program, and being able to define the services played for each program would give an even more accurate sense of that musicians involvement week-to-week. 
