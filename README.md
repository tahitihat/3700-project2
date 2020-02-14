# CS3700 Project 2 - Team Blonco

Caitlin Wang and Isabel Tripp

## High-level Approach

### Milestone

We started this project by looking at the milestone test cases and making sure we had a shared understanding about how our router should behave. Talking through how to route each of the different packets that would be sent to us led to success when actually implementing our router. Using the provided starter code, we wrote functions to handle the different messages we would encounter (update, data, and dump). The errors thrown by the simulator helped us spot bugs and discover any holes in our understanding. Finally, after our program successfully passed the level 1 tests, we cleaned up our implementation and added necessary error handling.

### Remaining Project

For the remainder of Project 2 we followed the steps detailed in the assignment description and implemented revoke messages, peering relationships, longest prefix matching, and route aggregation, one by one. Our approach to implementing each of these new features was to talk out loud about our strategy and write out pseudo-code. After we outlined a plan, writing working code became straightforward. On more than one occasion, we had to refactor our code, either to support new features or to abstract functionality. After each refactor, we made sure our tests were still passing, so as to reduce the amount of debugging when working on larger changes.

## Challenges

### Milestone

1. At a high level, the most challenging part of this assignment thus far has been understanding the complex assignment spec and figuring out some of the more intricate details of how core Internet infrastructure works (one of the stated objectives of project 2)! Specifically, neither of us fully understood CIDR notation and the purpose of network masks. It's safe to say that we're now more comfortable with that material. And although the amount of implementation was minimal for this milestone assignment, we put in time to understand what we'll need to do to complete the full project -- hopefully this helped inform some of our design decisions, and we won't have to refactor too much as we move forward.

2. For a while, we were stuck on forwarding update announcements to our router's neighbors. Running the simulator led to 'Unexpected Message on Interface' errors. Iteratively, we figured out that we had to (1) change some of the the content in the update packet, (2) not re-send the packet to the router it came from, and (3) send the packet from the correct IP for the packet's destination.

### Remaining Project

1. Up until we implemented route aggregation, each entry in our routing table had a `(network, netmask)` tuple key, where the value of each key was an array of all the ports that network could forward data to. However, when we started to implement route aggregation, we realized it would be difficult to coalesce two routes since every port we could forward to did not have a unique entry in our forwarding table. Therefore, we decided to modify our `self.routes` table to the following structure:

    ```
    # route is the IP address/port that can reach the network
    self.routes = {(network, netmask, route): {'localpref': '', 'ASPath': '', 'origin': '', 'selfOrigin': ''}, ...}
    ```
    This was a challenging design choice, especially since we had already implemented all other features with our previous routing table structure. In the end, we decided it made sense to flatten our table as described above so that aggregating routes could be a simpler task. 

2. While developing, we occasionally got tripped up by Python's pass-by-reference nature and were unknowingly mutating objects. This led us to store incorrect values and fail a few tests. We spent some time debugging those issues and were challenged to develop a deeper understanding about the language semantics. 

## Testing

The simulator file (http://course.khoury.neu.edu/cs3700sp20/archive/bgp-sim.tar.gz) was extremely helpful for testing network activity. In addition, we wrote code with focused print statements and used our local python interpreter to test python syntax and libraries such as ipaddress.
