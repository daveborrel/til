# Twitter Fanning Out

Twitter ran into an issue when querying the user's timeline because it would "Fan Out". To work around this, when users would post a tweet, each new tweet would be delivered to each user's mailbox.

```sql
SELECT tweets., users. FROM tweets
 JOIN users ON tweets.sender_id = users.id
 JOIN follows ON follows.followee_id = users.id
 WHERE follows.follower_id = current_user
```

What each step does

`SELECT tweets., users. FROM tweets` 
- For each record in tweets and users, give me all the columns. Then make tweets the base table.

`JOIN users ON tweets.sender_id = users.id` 
-  Add user details to each tweet by matching tweets.sender_id with users.id

`JOIN follows ON follows.followee_id = users.id` 
- Add follower information by matching users.id with follows.followee.id

`WHERE follows.follower_id = current_user` 
-  Only keeps the rows that have the current user.


### Sources

[DDIA](https://www.amazon.ca/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)