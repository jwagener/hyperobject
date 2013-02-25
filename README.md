# HyperObject (TBD)
___Placeholder Project - Not started yet - Feedback welcome___

a library to extract information about all the url:s!

taglines:
If the semantic web doesn't come to you, you gotta do it yourself
I don't wanna deal with your shitty API.

## Mission Statement

Create a library to lookup information for any URLs through the use of various strategies. Each of these strategies can provide a specialisation for certain URLs. By giving estimates about cost and accuracy the library or user of such can make an informed decision about which strategies to pick.

The strategies should be formalised in a way that allows easy reimplementation of the library in various languages. And of course supported by tests (test against offline html and live URL:s)

The end result should follow a well known schema of the extracted information (name, title, html etc..) plus the raw result that is specific to each strategy (which can change in the future...).

## Possible Strategies

- Facebook Open Graph
- Wikipedia
- Youtube (maybe even using get_video_info to access raw streams, but these are signed to the requester's ip address)
- Vimeo
- SoundCloud API (using resolver, pass client_id or oauth_token)
- Facebook Graph (need token)
- oEmbed
- Instapaper
- RSS
- RDF
- Embed.ly

## Schema

name:  a proper name for the object (not the document title, without author information)
title: a composed title "Flickermood by Forss", "Flickermood by Forss on SoundCloud"

description: a 1-2 sentence description
images: images usable for previews. 1st image should be the best representation of that object
url: canonical url of this object
machine_url: api url of this object ?
provider: "twitter"
provider_object_id: tweet_id
created_at:
html: an embeddable representation of this object.
author
	("user" object), (multiple?)
	url:
	machine_url:
	images:
	name:

weirdos:
	popularity/likes/comment/visits/plays count and that shit. 

seperated:

html_generator: a helper to call to generate embeddable html with options like width, height, auto play etc?

raw: raw response of this url.
raw_machine: raw api response
urls: urls of this object (for example


## API

HyperObject.httpClient =

HyperObject.Strategies.Facebook.client_id = "bla"

ho = HyperObject.get("..") # just creates a new fucking instance.
hyper_object = new HyperObject("http://youtube.com/watch?bla", options: {strategies: "Facebook", proxy: httpProxy (also to work around cross domain issues in client side js)})

HyperObject.Stragegies.Facebook
	#ready: -> @client_id != null -> if it requires certain shit
	#estimate: (url, options) -> {accuracy: 0-1, cost: 0-1} 
  # calculate url, options can include the required fields. so maybe cost 0 to just get a youtube embed html and accuracy 1.0
  #get: (url,options) -> #BOOM! ruby -> sync get, javascript -> promise

If multiple strategies are used let the result trickle down,
to reuse raw response + extend fields that one or the other strategy couldn't lookup.

HttpProxy.get
HttpProxy.post / put / delete
(how could it whitelist certain domains like youtube.com/get_video_info for core?)

HyperObject.Stragegies.Facebook

get() -> UrlRewrite -> Mapping

## Inspiration

- Geocoder
  - Uses strategies
  - Has a kickass website / documentation.
- Omniauth 
  - Uses strategies

## Languages

- Ruby Gem
- Javascript (through a cross domain proxy if necessary?)


	