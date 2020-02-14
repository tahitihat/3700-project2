# CS3700 Project 2 - Team Blonco

Caitlin Wang and Isabel Tripp

## High-level Approach

### Milestone

We started this project by looking at the milestone test cases and making sure we had a shared understanding about how our router should behave. Talking through how to route each of the different packets that would be sent to us led to success when actually implementing our router. Using the provided starter code, we wrote functions to handle the different messages we would encounter (update, data, and dump). The errors thrown by the simulator helped us spot bugs and discover any holes in our understanding. Finally, after our program successfully passed the level 1 tests, we cleaned up our implementation and added necessary error handling.

### Remaining Project

- Going in order of project assignment steps
- Talking through implementation and writing pseudo-code before actually implementing new features
- Refactoring as we go, making sure our code still works after each refactor

## Challenges

### Milestone

1. At a high level, the most challenging part of this assignment thus far has been understanding the complex assignment spec and figuring out some of the more intricate details of how core Internet infrastructure works (one of the stated objectives of project 2)! Specifically, neither of us fully understood CIDR notation and the purpose of network masks. It's safe to say that we're now more comfortable with that material. And although the amount of implementation was minimal for this milestone assignment, we put in time to understand what we'll need to do to complete the full project -- hopefully this helped inform some of our design decisions, and we won't have to refactor too much as we move forward.

2. For a while, we were stuck on forwarding update announcements to our router's neighbors. Running the simulator led to 'Unexpected Message on Interface' errors. Iteratively, we figured out that we had to (1) change some of the the content in the update packet, (2) not re-send the packet to the router it came from, and (3) send the packet from the correct IP for the packet's destination.

### Remaining Project

1. Deciding on routing table data structure
2. Unintentionally utating variables
3. IP Address manipulation in aggregation implementation

## Testing

The simulator file (http://course.khoury.neu.edu/cs3700sp20/archive/bgp-sim.tar.gz) was extremely helpful for testing network activity. In addition, we wrote code with focused print statements and used our local python interpreter to test python syntax and libraries such as ipaddress.
