---
layout: post
title:      "CLI Data Gem Portfolio Project"
date:       2020-08-06 21:29:43 +0000
permalink:  cli_data_gem_portfolio_project
---


I decided to focus my CLI Data Gem project on the Houston Symphony website.

Most orchesta websites are clunky at best, and impossible to navigate quickly at worst. I decided to create a program that would scrape data from upcoming concerts from the website and provide a neat and tidy presentation of the important details through the command line. Additionally, I wanted to allow the user of my application to search for their favorite composer, and return a list of concert programs that they could easily select and view more details about.

I first created my basic gem structure using the `bundle` method. This was a great learning experience to be tasked with the basic file structure that was always a given through the Learn coursework so far. My first attempt at the folder structure used the gem name "houston-symphony-concert-cli", but this created a rather confusing nest of folders. I ended up circling back to this setup method after writing a few classes, and arrived at a more concise folder structure. Towards the end of my project, I moved all the class files into a module, which allowed me to clean up the folder structure further, but required rather messy method calling in the CLI class. If I had to start again from scratch, or had another week to continue refactoring, I would choose a much tidier module name.

I started my work on the scraper method. After poking around https://houstonsymphony.org/tickets/concerts/ with the inspect tool and trying some different selectors, I found that I could scrape both the concert dates and a descriptive title for the concert. I also worked out a way to store a "program url" that a second scraper method could use to collect a detailed description and a list of pieces and their composers.

Then I formed classes to describe and keep track of each Concert, Composer, and Piece. Similar to the music library lab, each Composer had many Pieces. In addition, each Concert had many Composers and Pieces. My first few versions of the code to transfer from the scraper to each class centered around the scraper creating a hash with the necessary data. As I refactored, this process obviously slowed down the scraping process, so I added `create_or_find_by_name` methods to the Composer and Piece classes. Plugging the scraped information directly into a call for a new instance of each class halved the "load" time of the concert database.

After getting the classes to play well together, it was on to the CLI. I had been using the `bin/console` command to run tests on the classes as I wrote, so this file was quite messy. I ended up creating a new class for the CLI to hold the many methods I had in mind, leaving the console folder nice and clean.

I knew I wanted the user to be able to search through all Concerts for a specific Composer, but my first task was to simply create a display function to `puts` out the details of any Concert. Simply iterating through each Concert's Composers allowed me to output an array of Concert dates that included the desired Composer. Selecting a concert for further details simply calls the display method on that concert. 

The other two main options on the menu were more straightforward: displaying the next upcoming concert was simply displaying the first Concert from the list of all Concerts, and a straightforward list of all scraped concerts which could be selected for more details.

During this process I continued going back to the video resources in the assignments page for reference. I think I would have ended up spending much less time refactoring overcomplicated code if I had started from the CLI side and then working backwards, rather than starting at the scraping methods. Writing first the simple code that I "wish I had" would have saved me the trouble of over-engineering solutions to a few problems, and cut right to the utility that the many interconnected classes provide.

I also had some struggles using the sandbox IDE to code my program. This browser based system is very useful when loading up a small lab with everything ready to code, but it proved clunky when trying to load my code back up after a break, or if the wifi connection was lost. I spent many afternoons re-coding certain chunks because they had been lost to a wifi disconnect!

My other frustration with this project was based on the inconsistent formatting of the Houston Symphony website. After finding a very tidy chain of css selectors to differentiate the Composer and Piece names on certain pages, I discovered that some of the concert detail pages did not use the same parent-child relationship between these items. I had to create a second high level if/else flow to avoid scraping musician names or piece names as Composers, and these pages did not allow me to include the piece data for those concerts. Even without this, the functionality of the composer search still worked, but the scraping method became very clunky with so many if/else flow controls. 

I would love some feedback on my scraper methods. This is where I thought the program could still be streamlined, as scraping the entire season (40ish concerts) takes nearly a minute. Perhaps a more conscice css selector would also be able to differentiate between the Composers and Pieces on those pages where the piece names are not contained in a separate 'b' container. 

Overall it was a very satisfying process to go from a blank slate to a program that pulls interesting data from a website I use very frequently, and populate a series of classes allowing for easy searchability. I can't wait to see what is next and start working in a localized environment!
