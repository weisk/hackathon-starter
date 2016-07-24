Original Post:
[medium](https://medium.com/unboxd/how-i-built-an-app-with-500-000-users-in-5-days-on-a-100-server-77deeb238e83)

---

> Thor
Congrats! Obviously, efforts over your entire career prepared you to capture this opportunity so effectively. It would be great to hear more about your NodeJS stack. Also, how did you get through the app approval process so quickly?


> Erik Duindam
Thank you, Thor. Let me answer both of your questions separately.
The NodeJS stacks for GoSnaps and Unboxd (our main app) are both quite different. GoSnaps is really just this hackathon boilerplate, with most of the boilerplate code stripped and with some controller and model code added. It’s really not much more than NodeJS on ExpressJS with MongoDB via Mongoose. On the server I run Nginx as a reversed proxy to NodeJS. Right now I run forever to keep my Node processes up, even though I strongly prefer Systemd. Forever was just quicker to install :-) (MVP!). I use Node’s cluster to spawn NodeJS forks on multiple CPU cores. It’s a good practice to not do it on all CPU cores and leave 1 core dedicated for the OS in case of a 4+ core system.
Unboxd was originally built to be able to be a remote control to online video, so a second screen application. We had to do send small messages over sockets as quickly as possible, similar to chat. Therefore it’s set up with NodeJS and Cassandra, with ZeroMQ for message distribution and later Apache Kafka for message distribution. It uses Redis for a couple of rankings/leaderboards, because Redis is the only system really good at that. It’s set up with Varnish for possible static content and Nginx as a general reversed proxy.
In terms of Apple’s approval process, they are very quick these days. Apple made internal changes this year and now has an average approval time of approximately 24 hours. We were not a special case by any means.

---
