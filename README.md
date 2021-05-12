# Authors
- Simon Schønberg Bojesen
- Kenneth Hansen
- Frederik Blem
- Martin Høigaard Cupello

## Datamodel.
We have implemented Users and Posts in redis as hashmaps.<br>
Users have their username as the hashmap name like so: "@Simon"<br>
Each user has sets like so:<br>
1. "username", Swag
2. "firstname", Simon
3. "lastname", Bojesen
4. "passwordHashed", 2u39rnwejqe
5. "birthday", 1996-03-06

The postmap is named like so: "post:Simon"<br>
Each post in the map has the timestamp as the key, and the message as the value.

Followers and Following are both implemented in redis as lists, so we LPUSH when adding new followers.
These lists are keyed like so: "following:Simon" and "followedby:Simon"
We use LREM to remove specifically on the username.
