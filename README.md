# CS3700 Project 2 - Team Blonco
Caitlin Wang and Isabel Tripp

## High-level Approach

## Challenges
1. At a high level, the most challenging part of this assignment thus far has been understanding the complex assignment spec and figuring out some of the more intricate details of how core Internet infrastructure works (one of the stated objectives of project 2)! Specifically, neither of us fully understood CIDR notation and the purpose of network masks. It's safe to say that we're much more comfortable with that material now. And although the amount of implementation was small for this milestone assignment, we put in some time to understand the bigger picture of what we'll need to do to complete the full project -- hopefully this helped inform some of our design decisions, and we won't have to refactor too much as we move forward. 

2. For a while, we were stuck on forwarding update announcements to our router's neighbors. Running the simulator led to 'Unexpected Message on Interface' errors. Iteratively, we figured out that we had to (1) change some of the the content in the update packet, (2) not re-send the packet to the router it came from, and (3) send the packet from our router's correct IP for the packet dest.

## Testing
The simulator file (http://course.khoury.neu.edu/cs3700sp20/archive/bgp-sim.tar.gz) was extremely helpful for testing network activity. In addition, we developed through focused print statements and our local python interpreter (to test python syntax and libraries such as ipaddress). Note that we used the *old* simulator file for milestone 1 development, but will switch to the updated version moving forward. 