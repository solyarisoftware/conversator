# BOTmultiplexer
Route Telegram chat conversations from many users to many operators (both humans or bots) 

# Motivation / Goal
Working around conversational commerce messaging apps, I came with a typical help desk/customer care "problem": route incoming customers requestes to a pool of operators.

The gist is to realize a Telegram bot that act as *multiplexer* routing incoming users/customers requests to some operators, that could be or humans or bots applications (NLP-enabled to converstate with users).


# Architecture
The multiplecing logic could be decided by an *hypervisor/scheduler* (round robin routing among available operators). Profiling logics could be implemented easily.

```
       BOTMpx + dialog multiplexer
       +------+-------------------------------------------------------+
       |                                                              |
       |      +-----------------------------------------------+       | human admimnistrator
       |      | sw hypervisor logic / scheduler               +----------------------------+
       |      |                                               |       |
       |      +---------------------+--^----------------------+       |
       |                            |  |                              |
       |                            |  |                              |
       |      +---------------------v--+----------------------+       |
 user  |      |                                               |       | human operator
+-------------+ +---------------+         +-----------------> +----------------------+ Giorgio
       |      |                 |         |                   |       |
 user  |      |                 |         |                   |       | human operator
+-------------+ +---^     +---------------------------------> +----------------------+ Giuditta
       |      |     |     |     |         |                   |       |
 user  |      |     |     |     |         |                   |       | human operator
+-------------+ +---------------------------------+    +----> +----------------------+ Luca
       |      |     |     |     |         |       |    |      |       |
       |      |     |     |     |         |       |    |      |       |
       |      |     +----------------------------------+      |       |
       |      |           |     |         |       |           |       | bot operator instance
       |      |           |     |         |       +---------> +-----------------------------+
       |      |           |     |         |                   |       |
 user  |      |           |     |         |                   |       | bot operator instance
+-------------+ +---------^     ^---------------------------> +-----------------------------+
       |      |                           |                   |       |
 user  |      |                           |                   |       | bot operator instance
+-------------+ +-------------------------+                   +-----------------------------+
       |      |                                               |       |
       |      +-----------------------------------------------+       |
       |                                                              |
       +--------------------------------------------------------------+
```

# Code
**Ruby code coming soon!**
The Telegram bot logic is pretty simple: every user/operator is identified by a permenent `chat_id`, so `conversational sessions` statuses/profiling/routes data could be stored. 


# Contact
* **If you like this project, 1. VOTE it here!, 2: share&contribute 3: contact me**
* mail: [giorgio.robino@gmail.com](mailto:giorgio.robino@gmail.com)
* blog: [@solyarisoftware](http://www.twitter.com/solyarisoftware)
