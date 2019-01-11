# Video Streaming

Refer: netflex - https://www.youtube.com/watch?v=psQzyFfsUGU


Open Connect - Consitent Hashing
- Based on the top heat world wide
- Based on the top of specific country
- Based on the most recent viewed movie

ELB - Elastic Load Balance (AWS) - https://hackernoon.com/what-is-amazon-elastic-load-balancer-elb-16cdcedbd485 

> Problem: Customer from China connecting with the server in the U.S. --> high lantency
>
> Solution: Open connect dynamically check and connect the customer with the nearest server

> In Netflix: a top LB use round robin to choose the server in different zone (zone in different country). Then, zone will request the data via another LB which is to choose the server of different instance.

Video transcoding - it is needed because raw movie is really large (e.g. 50GB) and you need to save it in different server. By transcoding, we save a lot of space. To make the transcoding process faster and robustness, we can break the file into smaller chunck. Then trancoding in smaller chuncks and later merge then into a transcoded file.


![1](https://github.com/zhichengMLE/system-design/blob/master/_figs/video_transcode.png?raw=true)


Eventually, 
- When a customer is watching a movie, Open Connect will choose the best server to provide the service and detect customers' network speed. If the speed is slow, streaming with the lower resolution video. If the speed is fast, choose the higher one. 

- During the movie steaming, OC keep detecting the network and switch the resolution which eventually keep a relatively fast speed.

- The user data will capture to AWS, which further to use for recommendation system or machine learning, etc.
