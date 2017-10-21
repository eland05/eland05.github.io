---
layout: post
title:      "CLI Data Gem"
date:       2017-10-19 22:04:58 -0400
permalink:  cli_data_gem
---


I was super excited to take on this project, I have been waiting to have an opportunity to combine what I am doing here at Flatiron with my other passion of robotics.  I decided to scrape The Blue Alliance webpage, a well known source of data in the FIRST Robotics Competition world.  Crazy Excited!!!!

I put together my base code using fake data just to get all of my methods working correctly and communicating between my CLI and event object, then when I started putting together my scraper method I realized that The Blue Alliance uses HTML tables to present all of their data on their website.... Wow.... tables.  Not that I have anything against tables, the math and science teacher in me loves them and has preached to many middle school and high school students about their importance, but HTML tables and identifying the right selectors are a whole different ball game...

I watched the video of Avi scraping the Ruby Weekly page (also HTML tables) time and time again, pausing every other second to see every single thing he typed and if it could give me a small cue as to which selectors I should try next to parse the correct data needed for my CLI Gem App.  There were a couple of times I considered scraping a different page than The Blue Alliance, maybe one without all their data in HTML tables, but no, I was too excited about using The Blue Alliance and showing my CLI App to the kids on the high school robotics team I coach that I did not give up!

I finally found the right selectors to access the data I needed for my CLI App and was able to show it off to my students :)  I still struggled with geting my app to only collect the data about the current events and not include data from the next table on the page, so I limited it to only take in 5 rows of data, because it seems that The Blue Alliance typically list 5 current events for each week.  I know there is a better solution to this and continue to research, guess and check until I figure out a better way.  Here is the working event scraper method:

```
  def self.scrape_events
    doc = Nokogiri::HTML(open("https://www.thebluealliance.com/"))

    event_rows = doc.search("tr")[1..5]
    event_rows.each do |row|
      @@all << event = self.new
      event.name = row.search("td a").attr("title").text.strip
      event.date = row.search("td time").text
      event.location = row.search("td small").first.text
      event_site = row.search("td a").attr("href")
      event.site = "https://www.thebluealliance.com#{event_site}"
    end
  end
```

So today when I went to record my CLI Gem project walk through I realized that The Blue Alliance actually has 7 events listed for this week's events instead of 5, so I had to fix the code today, plus I knew if there were ever less than 5 events it would seriously break my code, so here is the updated code so that ensures the gem only scrapes the current number of current events.

```
  def self.scrape_events
    doc = Nokogiri::HTML(open("https://www.thebluealliance.com/"))

    event_table = doc.search("table.event-table")
    event_rows = event_table.search("tr")[1..-1]

    event_rows.each do |row|
      @@all << event = self.new
      event.name = row.search("td a").attr("title").text.strip
      event.date = row.search("td time").text
      event.location = row.search("td small").first.text
      event_site = row.search("td a").attr("href")
      event.site = "https://www.thebluealliance.com#{event_site}"
    end
  end
```
