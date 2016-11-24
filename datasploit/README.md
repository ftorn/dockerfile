Dataspoit
====================

## Installation

- To build the Dockerfile:
  - docker build -t datasploit .
- To run the container:
  - docker run --rm -it --network host --name dsploit datasploit
- To use datasploit:
  - docker exec -it dsploit bash
  - python datasploit/domainOsint.py -d YOURDOMAIN
- Remember:
  - you have to use your config.py
  - if you want persistence you have to use volume
