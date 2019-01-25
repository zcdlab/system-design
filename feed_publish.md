# Feed

## Feed Publishing

### Pull model (Fan-out-on-load)
This method involves keeping all the recent fee d data in memory so that users can pull it from the server whenever they need it. C lients can pull the feed data on a regular basis or manually whenever they need it. Possible problems with this approach are a) New data might not be shown to the user s until they issue a pull request, b) It’s hard to find the right pull cadence, as most of the time pull requests will result in an empty response if there is no new data, causing waste of resources.


### Push model (Fan-out-on-write)
For a push system, once a user has published a post, we can immediately push this post to all her followers. The advantage is that when fetching feed, you don’t need to go through your friends list and get feeds f or each of them. It significantly reduces read operations. To efficiently manage th is, users have to maintain a Long Poll request with the server for receiving the up dates. A possible problem with this approach is that when a user has millions of fo llowers (or a celebrity-user), the server has to push updates to a lot of people.


### Hybrid
Another interesting approach to handle feed data could be to use a hybrid a pproach, i.e., to do a combination of fan-out-on-write and fan-out-on-load. Specifi cally, we can stop pushing posts from users with a high number of followers (a cele brity user) and only push data for those users who have a few hundred (or thousand) followers. For celebrity users, we can let the followers pull the updates. Since th e push operation can be extremely costly for users who have a lot of friends or fol lowers therefore, by disabling fanout for them, we can save a huge number of resour ces. Another alternate approach could be that once a user publishes a post; we can limit the fanout to only her online friends. Also, to get benefits of both the appr oaches, a combination of push to notify and pull for serving end users is a great w ay to go. Purely push or pull model is less versatile.



## Feed Ranking


The most straightforward way to rank posts in a newsfeed is by the creation time of the po sts. But today’s ranking algorithms are doing a lot more than that to ensure “importan t” posts are ranked higher. The high-level idea of ranking is to first select key “signa ls” that make a post important and then figure out how to combine them to calculate a fin al ranking score.

More specifically, we can select features that are relevant to the importance of any feed item, e.g. number of likes, comments, shares, time of the update, whether the post has ima ges/videos, etc., and then, a score can be calculated using these features. This is genera lly enough for a simple ranking system. A better ranking system can significantly improve itself by constantly evaluating if we are making progress in user stickiness, retention, a ds revenue, etc.


## Feed Displaying
### How many feed items can we return to the client in each request? 

We should have a maximum limit for the number of items a user can fetch in one request (say 20). But we should let clients choose to specify how many feed items they want with each request, as the user may like to fetch a different number of posts depending on the device (mobile vs desktop).

### Should we always notify users if there are new posts available for their newsfeed?
It cou ld be useful for users to get notified whenever new data is available. However, on mobile devices, where data usage is relatively expensive, it can consume unnecessary bandwidth. H ence, at least for mobile devices, we can choose not to push data, instead let users “Pul l to Refresh” to get new posts.