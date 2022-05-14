Title: Chipotle 2.0!
Date: 2020-12-06
Category: Project
Tags: python, project, aws, chipotle, data, ec2
Slug: chipotle2.0
Authors: John Pham
Summary: Chipotle Analysis 2.0


# Data

My first ever project that I posted to my previous website was related to Chipotle, a place that I haven't been to in months since the pandemic after having been in my weekly lunch rotation. At the end of my [first blog post](http://www.phamiliar.com.s3.amazonaws.com/Paying%20the%20Price%20for%20Chipotle.htm), I mentioned a bit about finding price discrepancies between nearby locations to see if there are price arbitrage opportunities. Is there a preferred location for you to minimize costs?

## All Locations (Marker Colored by Price)
Zoom in and out of the map to see the price of steak burritos across the country. 
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/my_map.html"></iframe>
</div>


## Most Proximate Chipotle Locations
These are pairs of the nearest chipotle locations. Distance measures are calculated using latitude, longitude coordinates with a haversine distance approxmiation. I fully recognize that this straight distance measure does not reflect the effective distance -- people can't be expected to walk through walls or on water. 

<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_near_1_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_near_2_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_near_3_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_near_4_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_near_5_map.html"></iframe>
</div>

## Most Proximate Chipotle Locations with Different Prices
These are the nearest locations where there is a price different between goods. Again, this is caveated with the same conditions as the nearest locations. 
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_diff_1_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_diff_2_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_diff_3_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_diff_4_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_diff_5_map.html"></iframe>
</div>

## Greatest $ Saved Per Mile Between Chipotle Locations
These are the locations with the highest dollars saved per mile. These are places where it could be worthwhile for you to consider going to the cheaper location. Once again, straight line distance does not necessarily reflect the ease/opportunity cost of going to the other location.
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_dpm_1_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_dpm_2_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_dpm_3_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_dpm_4_map.html"></iframe>
</div>
<div class="iframe-chipotle-container">
  <iframe class="responsive-iframe" src="http://www.phamiliar.com.s3.amazonaws.com/chipotle/top_dpm_5_map.html"></iframe>
</div>



# Backstory

The first project featured a poorly coded for-loop with copy and pasted store ids in a massive list. The script that collected the store ids was separate from the script that collected the data. It was spaghetti code that I was too embarassed to share with anyone, and it was nearly impossible to repeatedly run the code. Also, there was no version control whatsoever. If you're eager to look at the code, let me know. I think there's a potential risk of bombarding the Chipotle API if I released into the wild.  The major differences between V1 and V2 are:

1. V1 could not be a fully scheduled and automated script. The intention of V2 was to have a fully automated pipeline that runs the script on ec2, pushes the outputs into s3, and queries and loads data from RDS. I hit the memory limits on the free tier EC2 instance so the analytical layer is still local, but the scraping runs on EC2, and assets are loaded to S3. I left out the RDS layer as it was overkill for this project. TLDR: V2 is only a few key strokes from fresh data.
2. V1 used selenium to click around and generate hundreds of online orders. I thought I was really clever at the time. Now V2 uses the Chipotle APIs. This enabled me to collect more data, faster.
3. V1 included my initial attempts to learn D3 and used the Google Fusion Tables API. V2 is much simpler with regards to data presentation (HTML Pandas tables) and the Folium library now that Fusion Tables are deprecated. Just wanted to get this out inaugural post out quick and move on to the next.




