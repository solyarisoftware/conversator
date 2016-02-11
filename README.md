# Conversator
Route Telegram chat conversations from many users to many operators (both humans or bots) 
[](https://upload.wikimedia.org/wikipedia/commons/e/e0/Telephony_multiplexer_system.gif)

> ** NOTE: This is just a DRAFT readme/manifesto**. I'll develop asap the real code (in Ruby language).

# Motivation / Goal
Working around conversational commerce messaging apps, and specifically thinking about a chat bot on the [telegram](http://www.telegram.org) instant messaging platform,  I face with a typical call center/help desk/customer care task: **to route incoming customers requests to a chat bot to a pool of operators**.

The gist here is to realize a bot framework that act as *multiplexer/demultiplexer* routing incoming users/customers requests to some **operators, that could be or humans or bots applications (NLP-enabled to converstate with users)**.

This is useful for a standard customer care scenario, where customers could contact a *contact center* (realized here through a Telegram bot account) to talk with an operator, to have any sort of *service*: getting some info, or to solve an issue with the help pf an expert (see healthcare assistance/patient monitoring), or to purchase something (conversational ecommerce).   

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

Routing have to be dynamic: as soon a conversation between an user and an operator end, the operator pass from state `busy` to `free` and could converse with a new user. A human operator could decide himself to become available for a new conversation (e.g. submitting a `/start` command to the hypervisor bot), and where a conversation is concluded (e.g. submitting a `/stop` command to the hypervisor bot). Afterall, with some implicit logic, a bot operator could do the same :-). 

```

              +-----------------------------------------------+   
              |  hypervisor logic / scheduler                 +--> human system admin
              |                                               |       
              +-----------------------------------------------+       
                                    |  ^                              
                                    v  |                              
              +-----------------------------------------------+       
 user         |                                               |      
 -----------> | <---------------+         +-----------------> | <-- human operator: Giorgio
              |                 |         |                   |       
 user         |                 |         |                   |        
 -----------> | <---+     +---------------------------------> | <-- human operator: Giuditta
              |     |     |     |         |                   |       
 user         |     |     |     |         |                   |        
 -----------> | <---------------------------------+    +----> | <-- human operator: Luca
              |     |     |     |         |       |    |      |       
              |     |     |     |         |       |    |      |       
              |     +----------------------------------+      |       
              |           |     |         |       |           |        
              |           |     |         |       +---------> | <-- bot operator, instance
              |           |     |         |                   |       
 user         |           |     |         |                   |      
 -----------> | <---------+     +---------------------------> | <-- bot operator, instance
              |                           |                   |       
 user         |                           |                   |       
 -----------> | <-------------------------+                   | 
              |                                               |       
              +-----------------------------------------------+       

```

# Code
**Ruby code coming soon!**<br>
The Telegram bot logic is pretty simple: every user/operator is identified by a permenent `chat_id`, so `conversational sessions` statuses/profiling/routes data could be stored. 


# Contact
* If you like this project, 
  1. **Give a START to the project here!**, 
  2. share and contribute!
  3. Contact me, via email
* mail: [giorgio.robino@gmail.com](mailto:giorgio.robino@gmail.com)
* blog: [@solyarisoftware](http://www.twitter.com/solyarisoftware)
