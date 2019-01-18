# Load Balancing

Ref: https://www.nginx.com/resources/glossary/load-balancing/

## Round Robin

Using round robin split equally of the incoming request to servers. But this doesn't take load of server into consideration, To handle this, a more intelligent LB solution can be placed that periodically queries backend server about their load and adjusts traffic based on that (use load to update weight, then Weighted Round Robin).

## Weighted Round Robin

Similar to Round Robin, but consider the weight of server.

## Least Connection

Send the new request to the server with least connections.

## Ip Hashing

Ues the ip address to determine which server to connect.

## Special Cases

- Facebook Messenger: We need a load balancer in front of chat servers; that can map each UserID to a server that holds the connection for the user and then direct the request to that server. Similarly, we would need a load balancer for our cache servers.
