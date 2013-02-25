# HyperObject (TBD)

___Placeholder Project - Not started yet___

## Mission Statement

Create a library to lookup information for any URLs through the use of various strategies.
Each of these strategies would provide a specialization for certain URLs.
By giving estimates about cost and accuracy the library or user of such can make an informed decision about which strategy to pick.

The strategies should be formalized in a way to allow reimplementation in various languages and supported by tests.

The end result should follow a well known schema of the extracted information (name, title, embeddable_html, description, canonical url, provider id, provider name, author, author url, images, type etc..)
plus a raw result that is specific to each strategy (which might change in the future...).

## Possible Strategies

- Facebook Open Graph
- Wikipedia
- Youtube (maybe even using get_video_info to access to raw streams, but these are signed to the requester's ip adress, so browsers have to fetch it directly.)
- Vimeo
- oEmbed
- Embed.ly

## Languages

- Ruby Gem
- Javascript (through a cross domain proxy if necessary?)

## Inspiration

- Geocoder
  - Uses strategies
  - Provides a kickass website / documentation.
- Omniauth 
  - Uses strategies
