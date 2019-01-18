# Design a Web Crawl Application

Consider:
- what protocal are we looking at?
    - HTTP
    - FTP
    - Others

- What is the expected number of pages that we are going to crawl? How big will the database or storage become?
    - one page have millions of sub domain.

- Consider RobotsExclusion website.


Steps to crawl:

> BFS, DFS, and Path-ascending crawling (/a/b, /a/, / ....)

- Pick up a URL from unvisited URLs list.
- Determine the IP address of the domain
- Estabilish a connection to the host to downoad the corresponding document.
- Parse the document of content and look for new URLs.
- Add new URL to the list of unvisited URLs.
- Process the downloaded document - store if or indexes its contents.



