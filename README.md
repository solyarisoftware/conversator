# BOTmultiplexer
Route Telegram chat conversations from many users to many operators (both humans or bots) 

# Motivation / Goal
Working around conversational commerce messaging apps, I came with a typical help desk/customer care need: route incoming customers requests to a chat bot to a pool of operators.

The gist here is to realize a (Telegram) bot that act as *multiplexer* routing incoming users/customers requests to some operators, that could be or humans or bots applications (NLP-enabled to converstate with users).

This is useful for a typical customer care scenario, where customers could contact a *contact center* (realized here through a Telegram bot account) to talk with an operator getting some info, or to solve an issue, or to purchase something (conversational ecommerce).   

A bot act as a front-end to customers, 
* verifying id user is new, or retrieving his previous *session data*
* dispatching the incoming *messaging call* to a *back-end operator* 

The important point is: WHO is the *operator* ? 
* Operator is an Human operator
  Is really a person! A human being.
* Operator is a bot (again!)
  The bot talk with user in his natural language and the bot could substitute human operator to solve simple requests (depending on the context), chatting with user as "first level helpdesk".  

# Architecture
The multiplexing logic could be decided by an *hypervisor/scheduler* (round robin routing among available operators). Profiling  logics could be implemented easily. A profit scenario could foresee to let the user talk with a specific Person, maybe a very specilized operator, etc. etc.

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
**Ruby code coming soon!**<br>
The Telegram bot logic is pretty simple: every user/operator is identified by a permenent `chat_id`, so `conversational sessions` statuses/profiling/routes data could be stored. 


# Contact
* **If you like this project, 1. VOTE it here!, 2: share&contribute 3: contact me**
* mail: [giorgio.robino@gmail.com](mailto:giorgio.robino@gmail.com)
* blog: [@solyarisoftware](http://www.twitter.com/solyarisoftware)
