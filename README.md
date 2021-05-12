## Datamodel.

We have implemented Users and Posts in redis as hashmaps.
Users have their username as the hashmap name like so: "@Simon" 
Each user has sets like so:
"username", Swag
"firstname", Simon
"lastname", Bojesen
"passwordHashed", 2u39rnwejqe
"birthday", 1996-03-06

The postmap is named like so: "post:Simon"
Each post in the map has the timestamp as the key, and the message as the value.

Followers and Following are both implemented in redis as lists, so we LPUSH when adding new followers.
These lists are keyed like so: "following:Simon" and "followedby:Simon"
We use LREM to remove specifically on the username.
