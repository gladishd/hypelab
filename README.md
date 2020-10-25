# hypelab
twitch chat data and analysis





Hey Dean,

Here's the data. Some important background info on the label variables:

* 'liked' is a good clip
* 'disliked' is a bad clip
* 'done' means I watched the clip but it was neither good or bad
* 'liked' and 'done' means it's a pretty good clip but not a great clip. I think this combination is least important for now, so we should filter out highlights with both of these as true to start out with.

And info on the most important input columns:

* 'timestamp' is the number of seconds from the beginning of the VOD
* 'length' is the length of the highlight. You will need to use this and timestamp to gather the relevant chat data

I included other columns besides these two, but these are the only two you will need to create the input matrix for the model. I'm sending all the chat data we have for labeled highlights, each file name is the {vod_id}.csv. So to create the input data you'll need to first get the right `{vod_id}.csv` file and then filter using timestamp and length as described above.

For the model features, I think first it makes sense to keep it simple and to do a bag of words. After that, I think ultimately TF-IDF will yield better results but that will be an interesting experiment to test. If you find any other good NLP methods it would be sick to see what results those give us, from my understanding bag of words and TF-IDF are the most basic shit.

As far as what to model, the best place to start is to first build a model to predict whether a highlight is 'disliked' or not. we want to avoid showing these highlights completely and my hunch is that this will probably be our cleanest model. For example, most of the disliked highlights are stream technical issues like when the streamer's mic isn't working so a bunch of people in chat are spamming "mic", "check mic" or whatever.

Next, I think it makes sense to see if a model can predict whether a model will be 'liked' or just 'done'. So we want to see if we can filter out great highlights from ok highlights. For this model we would filter out all 'disliked' highlights and any highlights that are both 'liked' and 'done'.

There are lots of other things to experiment with. After we assess the generalized model, I think it might make sense to make a model per game, so one model to predict 'liked' or just 'done' for Rocket League for example. I'm guessing we only have enough data for rocket league to make this model right now.

This project is very complex IMO, so just want you to know that there aren't any dumb questions and you can ask me about anything. 

LESGETTIT
-Chris
